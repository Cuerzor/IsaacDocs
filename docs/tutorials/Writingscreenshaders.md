---
tags:
  - 教程
---
# [教程] 编写屏幕着色器

## Example Shaders:
* Tilt Shift Shader by im_tem: [https://steamcommunity.com/sharedfiles/filedetails/?id=2524003926](https://steamcommunity.com/sharedfiles/filedetails/?id=2524003926)
* Vortex Street background shader by Wofsauge [Preview Video](../customData/Vortex_Street_shader.mp4) - [Code](../customData/vortex_street_shader.zip) - [Original shader source](https://www.shadertoy.com/view/MlS3Rh)

## Create your own shader:

**重新加载mod的着色器可以通过控制台命令：** `reloadshaders`

为了写你的屏幕着色器，你需要在**Mod文件夹**中的_content_文件夹里创建'_shaders.xml_'.

shaders.xml 应当有如下结构：

```xml
<shaders>
    <shader name="SHADER_NAME">
        <parameters>
            <param name="PARAMETER_NAME" type="PARAMETER_TYPE"/>
            ...
        </parameters>
        <vertex><![CDATA[
            VERTEX_SHADER
        ]]></vertex>
        <fragment><![CDATA[
            FRAGMENT_SHADER
        ]]></fragment>
    </shader>
    <shader name="...">
        ...
    </shader>
</shaders>
```

where:

*   `SHADER_NAME` 是你着色器的名称.
*   `PARAMETER_NAME` 是你想从Lua传递的每个自定义参数的名称.
*   `PARAMETER_TYPE` 是以下之一：`float`，`vec2`，`vec3`，`vec4`
*   `VERTEX_SHADER` 是你的顶点着色器，应该始终包含这些属性:


```xml
attribute vec3 Position;
attribute vec4 Color;
attribute vec2 TexCoord;
attribute vec4 RenderData;
attribute float Scale;
...your attributes...
uniform mat4 Transform;
...
```

*   `FRAGMENT_SHADER` 是你的片段着色器，应该至少包含以下内容：

```xml
varying lowp vec4 Color0;
varying mediump vec2 TexCoord0;
varying lowp vec4 RenderDataOut;
varying lowp float ScaleOut;
uniform sampler2D Texture0;
```

`RenderData.xy` 包括窗口大小，而 `RenderData.zw` 是纹理大小。

`Scale` 包含基于窗口大小的Isaac房间缩放比例。当你调整窗口大小时，你可以看到缩放的效果，游戏内容在一定像素范围内保持固定，然后跳转到另一个缩放级别。

由于引擎限制，我们只能通过顶点着色器传递数据。

## Shader Example Code:

一个带有自定义参数的着色器示例，它根据玩家位置和游戏内帧计数器改变屏幕的颜色色调。

Code: [→ Download this example mod here ←](../customData/shader_example_mod.zip)

<figure class="video_container">
  <video controls="true" allowfullscreen="true" style="width:25rem">
    <source src="../customData/shader example preview.mp4" type="video/mp4">
  </video>
  <figcaption>Result of this shader.</figcaption>
</figure>


```xml

	<shaders>
		<shader name="RandomColors">
			<parameters>
				<param name="PlayerPos" type="vec2"/>
				<param name="Time" type="float"/>
			</parameters>
			<vertex><![CDATA[
				attribute vec3 Position;
				attribute vec4 Color;
				attribute vec2 TexCoord;
				attribute vec4 RenderData;
				attribute float Scale;
				attribute vec2 PlayerPos;
				attribute float Time;
				varying vec4 Color0;
				varying vec2 TexCoord0;
				varying vec4 RenderDataOut;
				varying float ScaleOut;
				varying vec2 PlayerPosOut;
				varying float TimeOut;
				uniform mat4 Transform;
				void main(void)
				{
					RenderDataOut = RenderData;
					ScaleOut = Scale;			// Passing data to fragment shader
					PlayerPosOut = PlayerPos;	// Passing data to fragment shader
					TimeOut = Time;				// Passing data to fragment shader
					Color0 = Color;
					TexCoord0 = TexCoord;
					gl_Position = Transform * vec4(Position.xyz, 1.0);
				}
			]]></vertex>
			<fragment><![CDATA[
				varying lowp vec4 Color0;
				varying mediump vec2 TexCoord0;
				varying lowp vec4 RenderDataOut;
				varying lowp float ScaleOut;
				varying mediump vec2 PlayerPosOut;
				varying lowp float TimeOut;
				uniform sampler2D Texture0;
				void main(void)
				{
					vec4 Color = Color0 * texture2D(Texture0, TexCoord0);
					Color.r *= PlayerPosOut.x * 0.5f;
					Color.g *= PlayerPosOut.y * 0.5f;
					Color.b *= sin(TimeOut * 0.1f);
					gl_FragColor = Color;
				}
			]]></fragment>
		</shader>
	</shaders>

```
为了传递参数我们使用如下Lua代码：
```lua

local mod = RegisterMod("ShaderMod", 1)
function mod:GetShaderParams(shaderName)
	if shaderName == 'RandomColors' then
        local playerPos = Isaac.GetPlayer().Position
        local params = {
            PlayerPos = {   playerPos.X / 100.0,
                            playerPos.Y / 100.0 },
                            Time = Isaac.GetFrameCount()
            }
        return params;
    end
end
mod:AddCallback(ModCallbacks.MC_GET_SHADER_PARAMS, mod.GetShaderParams)
```
