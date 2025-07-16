---
tags:
  - Enum

search:
  boost: 3
---
# Enum "ModCallbacks"

Execution order diagram: [![callback diagram](../images/infographics/Isaac Callbacks.svg){: width='500' }](../images/infographics/Isaac Callbacks.svg)

## 有关回调的注意事项

首先，最好不要在高频回调如MC_NPC_UPDATE，MC_INPUT_ACTION中在不加限制的情况下使用如spawn等函数，否则将会导致游戏卡顿等问题

Value表示回调的序号

Name表示回调的名称

Function Args表示可以在Function中定义的变量

Optional Args表示可供筛选的变量

Return Type表示返回值的类型

???- example "Example Code"

    function mod:example(_,_,Ent_Player) --注意，Fun Arg必须按顺序，所以要用到后面的变量但前面的没有用处时可以用"_"或其他变量名替代而非直接在第一个处当后面的变量使用
        if Ebt_player:GetPlayerType() == 4 then
            print("小蓝人使用了D6？！")
        end
    end
    mod:AddCallback(ModCallbacks.MC_USE_ITEM, mod.example, CollectibleType.COLLECTIBLE_D6)--在最后的“CollectibleType.COLLECTIBLE_D6”即限定了只有主动道具D6被使用时该函数才会被调用

### MC_NPC_UPDATE {: .copyable }

在NPC更新后调用。

返回任何值都不会影响后续回调的执行。

???- warning "警告"

    当NPC播放“出现”动画时，此回调不会触发。例如，当一个裂口魔生成时，它会在第1帧触发，然后在第31帧及之后触发。

???- example "Example Code"

This code will print "Hello World!" for every NPC Update.

    ```lua
    function mod:myFunction(entity) -- 'entity' contains a reference to the NPC
        print("Hello World!")
    end
    mod:AddCallback(ModCallbacks.MC_NPC_UPDATE, mod.myFunction)
    ```

    This function will only print "Gaper found", if the NPC is of the type "ENTITY_GAPER".

    ```lua
    function mod:myFunction2(entity) -- 'entity' contains a reference to the NPC
        print("Gaper found!")
    end
    mod:AddCallback(ModCallbacks.MC_NPC_UPDATE, mod.myFunction2, EntityType.ENTITY_GAPER)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|0 |MC_NPC_UPDATE {: .copyable } | ([EntityNPC](../EntityNPC.md))|[EntityType](EntityType.md) | void |

### MC_POST_UPDATE {: .copyable }

在每次游戏更新后调用。

返回任何值都不会影响后续回调的执行。

???- info "执行信息"

    此回调每秒调用30次。当游戏暂停时（例如在屏幕过渡或暂停菜单时），它不会被调用。

???- example "Example Code"

This code will print "Hello World!" for every Game Update.

    ```lua
    function mod:myFunction()
        print("Hello World!")
    end
    mod:AddCallback(ModCallbacks.MC_POST_UPDATE, mod.myFunction)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|1 |MC_POST_UPDATE {: .copyable } | - | - | void |

### MC_POST_RENDER {: .copyable }

在每次游戏渲染后调用（每秒60次）。

返回任何值都不会影响后续回调的执行。

???- info  "执行信息"

    强烈建议仅在需要渲染某些内容时使用此函数。不建议将此函数用于不经常使用或需要持续重新计算的事情。

???- example "Example Code"

This code will print "Hello World!" everytime the game renders.

    ```lua
    function mod:myFunction()
        print("Hello World!")
    end
    mod:AddCallback(ModCallbacks.MC_POST_RENDER, mod.myFunction)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|2 |MC_POST_RENDER {: .copyable } | - | - | void |

### MC_USE_ITEM {: .copyable }

当使用主动道具时，或者当任何道具通过`EntityPlayer.UseActiveItem`传递时调用。

道具的[RNG](../RNG.md)允许为道具的随机事件设置种子。

返回`true`以显示“使用道具”动画，否则返回`false`。返回任何值都不会影响后续回调的执行。

如果返回的是一个表而不是布尔值，则可以将以下字段设置为非`nil`值以实现额外功能：

* Discharge：确定道具使用后是否应消耗充能。
* Remove：确定道具使用后是否应从玩家处移除。
* ShowAnim：如果设置为`true`，则播放默认的使用动画（相当于在AB+中简单地返回`true`）。

???- info "注意"

    “Discharge”字段决定了美德之书是否应该生成一个小精灵。将其设置为`false`可以防止小精灵生成。

???- example "Example Code"

This code will print "Hello World!" everytime an active item is used.

    ```lua
    function mod:myFunction(collectibleID, rngObj, playerWhoUsedItem, useFlags, activeSlot, varData)
        print("Hello World!")
    end
    mod:AddCallback(ModCallbacks.MC_USE_ITEM, mod.myFunction)
    ```

    This code showcases how the return value can be used to alter the behavior of the item usage. Here, it will cause the item to not discharge, not be removed on use and not show the use animation.

    ```lua
    function mod:myFunction2(collectibleID, rngObj, playerWhoUsedItem, useFlags, activeSlot, varData)
        return {
            Discharge = false,
            Remove = false,
            ShowAnim = false,
        }
    end
    mod:AddCallback(ModCallbacks.MC_USE_ITEM, mod.myFunction2)
    ```

    This code will only print "D6 used!" when the D6 is used.

    ```lua
    function mod:myFunction3(collectibleID, rngObj, playerWhoUsedItem, useFlags, activeSlot, varData)
        print("D6 used!")
    end
    mod:AddCallback(ModCallbacks.MC_USE_ITEM, mod.myFunction3, CollectibleType.COLLECTIBLE_D6)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|3 |MC_USE_ITEM {: .copyable } | ([CollectibleType](CollectibleType.md),<br>[RNG](../RNG.md),<br>[EntityPlayer](../EntityPlayer.md),<br>[UseFlags](UseFlag.md) [int],<br>[ActiveSlot](ActiveSlot.md),<br>CustomVarData [int])|[CollectibleType](CollectibleType.md) | boolean |

### MC_POST_PEFFECT_UPDATE {: .copyable }

在每个玩家每帧评估必须持续评估的道具效果后调用。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|4 |MC_POST_PEFFECT_UPDATE {: .copyable } | ([EntityPlayer](../EntityPlayer.md))|[PlayerType](PlayerType.md) | void |

### MC_USE_CARD {: .copyable }

当使用卡牌/符文时调用。

返回任何值都不会影响后续回调的执行。

???- example "Example Code"

This code will print "Hello World!" everytime any card is used.

    ```lua
    function mod:myFunction(cardID, playerWhoUsedItem, useFlags)
        print("Hello World!")
    end
    mod:AddCallback(ModCallbacks.MC_USE_CARD, mod.myFunction)
    ```

    This code will only print "Fool card used!" when the Fool card is used.

    ```lua
    function mod:myFunction2(cardID, playerWhoUsedItem, useFlags)
        print("Fool card used!")
    end
    mod:AddCallback(ModCallbacks.MC_USE_CARD, mod.myFunction2, Card.CARD_FOOL)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|5 |MC_USE_CARD {: .copyable } | ([Card](Card.md),<br>[EntityPlayer](../EntityPlayer.md),<br>[UseFlags](UseFlag.md) [int]|[Card](Card.md) | void |

### MC_FAMILIAR_UPDATE {: .copyable }

每个小精灵每帧都会调用。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|6 |MC_FAMILIAR_UPDATE {: .copyable } | ([EntityFamiliar](../EntityFamiliar.md))|[FamiliarVariant](FamiliarVariant.md) | void |

### MC_FAMILIAR_INIT {: .copyable }

在小精灵初始化后立即调用。

返回任何值都不会影响后续回调的执行。

???- warning "警告"

    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_PEFFECT_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|7 |MC_FAMILIAR_INIT {: .copyable } | ([EntityFamiliar](../EntityFamiliar.md))|[FamiliarVariant](FamiliarVariant.md) | void |

### MC_EVALUATE_CACHE {: .copyable }

当玩家的属性重新评估时调用一次或多次。例如，当玩家拾取一个提供属性的收集品道具或使用属性药丸时，此回调将触发。

可选参数可用于指定一个`CacheFlag`。它必须是一个单一的`CacheFlag`，两个或多个`CacheFlag`的组合将不起作用。

返回任何值都不会影响后续回调的执行。

使用此回调来实现任何改变玩家属性、小精灵、飞行能力、武器等的功能。

自定义收集品和饰品在“items.xml”文件中使用“cache”标签注释它们影响的特定属性。例如，一个增加眼泪射速和伤害的自定义被动收集品应该在“items.xml”条目中包含类似以下的内容：

```xml
  <passive
    name="Foo"
    description="My cool item"
    gfx="foo.png"
    cache="damage firedelay"
  />
```

有了这个条目，当玩家拾取Foo道具时，`MC_EVALUATE_CACHE`回调将触发两次，一次是`CacheFlag.CACHE_DAMAGE`，一次是`CacheFlag.CACHE_FIREDELAY`。

在为任何模组效果触发回调之前，会应用原版道具和效果的属性。

您可以通过以下步骤在其他回调中强制触发此回调：1) 手动将适当的缓存标志添加到玩家，2) 调用`EntityPlayer.EvaluateItems`方法。例如：

```lua
-- 我的自定义道具每帧改变玩家的伤害
function barPostPEffectUpdate(player)
  player:AddCacheFlags(CacheFlag.CACHE_DAMAGE)
  player:EvaluateItems() -- 现在“MC_EVALUATE_CACHE”回调将触发。
end
```

请注意，传递给回调的值始终是`CacheFlag`枚举的精确值。它永远不会是两个或多个`CacheFlag`的组合。因此，在比较缓存标志时，应始终使用普通相等而不是按位运算符。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|8 |MC_EVALUATE_CACHE {: .copyable } | ([EntityPlayer](../EntityPlayer.md),<br>[CacheFlag](CacheFlag.md))|[CacheFlag](CacheFlag.md) | void |

### MC_POST_PLAYER_INIT {: .copyable }

在玩家实体初始化后调用。

可选参数可用于指定玩家变体。0 = 玩家，1 = 合作宝宝。

返回任何值都不会影响后续回调的执行。

???- warning "警告"

    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_PEFFECT_UPDATE`并在第一帧检查这些属性。

???- info "条件行为 [](#){: .reporplus .tooltip .badge }"

    如果在继续已保存的游戏时调用`EntityPlayer`的某些方法，此回调会导致这些方法静默失败。这种行为是Kilburn在忏悔DLC中故意添加的，以便模组开发者更容易为自定义角色添加初始道具。（这种行为消除了模组开发者使用过滤逻辑来区分新游戏/创世纪使用/合作生成和继续游戏的情况的需要。）

    已知以下`EntityPlayer`方法会失败：

    ```lua
    AddCollectible
    AddTrinket
    AddKeys
    AddCoins
    AddBombs
    AddGoldenBomb
    AddGoldenKey
    AddGigaBombs
    AddMaxHearts
    AddHearts
    AddBlackHearts
    AddSoulHearts
    AddRottenHearts
    AddBoneHearts
    AddGoldenHearts
    AddEternalHearts
    AddBrokenHearts
    AddCard
    AddPill
    AddPrettyFly
    AddJarFlies
    AddJarHearts
    AddSoulCharge
    AddBloodCharge
    AddPoopMana
    SetPocketActiveItem
    ```

    以下`EntityPlayer`方法已验证会继续触发：

    ```lua
    AddBlueFlies
    AddBlueSpider
    AddWisp
    AddItemWisp
    AddSwarmFlyOrbital
    AddFriendlyDip
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|9 |MC_POST_PLAYER_INIT {: .copyable } | ([EntityPlayer](../EntityPlayer.md))|PlayerVariant* | void |

### MC_USE_PILL {: .copyable }

当使用药丸时调用。

返回任何值都不会影响后续回调的执行。

???- example "Example Code"

This code will print "Hello World!" everytime any pill is used.

    ```lua
    function mod:myFunction(pillEffectID, playerWhoUsedItem, useFlags)
        print("Hello World!")
    end
    mod:AddCallback(ModCallbacks.MC_USE_PILL, mod.myFunction)
    ```

    This code will only print "Bad Gas Pill used!" when the Fool pill is used.

    ```lua
    function mod:myFunction2(pillEffectID, playerWhoUsedItem, useFlags)
        print("Bad Gas Pill used!")
    end
    mod:AddCallback(ModCallbacks.MC_USE_PILL, mod.myFunction2, PillEffect.PILLEFFECT_BAD_GAS)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|10 |MC_USE_PILL {: .copyable } | ([PillEffect](PillEffect.md),<br>[EntityPlayer](../EntityPlayer.md),<br>[UseFlags](UseFlag.md) [int])|[PillEffect](PillEffect.md) | void |

### MC_ENTITY_TAKE_DMG {: .copyable }

在应用新伤害之前调用。

如果实体具有`DAMAGE_COUNTDOWN`标志，它将在指定的持续时间内忽略任何其他`DAMAGE_COUNTDOWN`伤害。

如果实体或玩家应该承受伤害，则返回`true`或`nil`，否则返回`false`以忽略伤害。如果实体是[EntityPlayer](../EntityPlayer.md)，`DamageAmount`是玩家将承受的半心伤害的整数数量。否则，`DamageAmount`是生命值的数量。

???+ bug

    返回除`nil`以外的任何值将阻止后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|11 |MC_ENTITY_TAKE_DMG {: .copyable } | (Entity [[Entity](../Entity.md)],<br>Amount [float],<br>[DamageFlags](DamageFlag.md) [int],<br>Source [[EntityRef](../EntityRef.md)],<br>CountdownFrames [int])|[EntityType](EntityType.md) | boolean |

### MC_POST_CURSE_EVAL {: .copyable }

此回调在当前关卡计算其种子诅咒后但在强制诅咒应用或禁止诅咒移除之前触发（主要是由于挑战）。

如果玩家带着黑蜡烛效果进入关卡，则跳过此回调。

`Curses`是一个包含当前[诅咒](LevelCurse.md)的位掩码。如果返回一个数字，它将用作新的诅咒位掩码，覆盖原始的。使用`Isaac.GetCurseIdByName()`来获取诅咒ID。

如果返回一个数字，它将是后续执行回调的“Curses”参数。

???+ bug

    返回非整数或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|12 |MC_POST_CURSE_EVAL {: .copyable } | ([Curses](LevelCurse.md) [int]) | - | int |

### MC_INPUT_ACTION {: .copyable }

每当游戏轮询[ButtonAction](ButtonAction.md)输入时触发此回调，即使是同一动作，每帧也会触发多次。由于它与轮询有关，无论玩家是否实际按下任何特定输入，它都会触发。

此回调用于任意更改输入。例如，您可以完全禁用玩家按下某个按钮。或者，您可以强制玩家按下特定按钮，等等。如果您只想_读取_某个输入是否被按下，则不应使用此回调，而应在`MC_POST_RENDER`回调中使用`Input.IsActionTriggered`方法。

此回调不会影响任何通过`Input`类读取用户输入的自定义模组代码。

* [Entity](../Entity.md) - 请求输入的实体。大多数情况下，这将是一个玩家。但是，如果输入不是从实体类读取的，或者是由好友探测器控制的实体，则它也可以为`nil`。
* [InputHook](InputHook.md) - 这决定了正在轮询的输入类型。这对应于`Input.IsActionTriggered`、`Input.IsActionPressed`和`Input.GetActionValue`方法，这些方法会触发此回调。

如果您不想覆盖输入，则返回`nil`。如果您想覆盖输入，则对于`IS_ACTION_PRESSED`（0）和`IS_ACTION_TRIGGERED`（1）输入钩子，必须返回一个布尔值；对于`GET_ACTION_VALUE`（2）输入钩子，必须返回一个介于0.0和1.0之间的浮点数。

返回任何值都不会影响后续回调的执行。

???- info "执行信息"

    此回调每秒大约调用1470次。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|13 |MC_INPUT_ACTION {: .copyable } | ([Entity](../Entity.md),<br>[InputHook](InputHook.md),<br>[ButtonAction](ButtonAction.md))|[InputHook](InputHook.md) | boolean or float |

### MC_LEVEL_GENERATOR  {: .copyable }

???+ bug

    此回调目前不起作用，游戏永远不会调用它！

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|14 |MC_LEVEL_GENERATOR  {: .copyable }  | - | - | void |

### MC_POST_GAME_STARTED {: .copyable }

当您开始游戏时调用此函数。当您继续游戏时，布尔值为`true`；当您开始新游戏时，布尔值为`false`。

此回调将在`MC_POST_NEW_ROOM`和`MC_POST_NEW_LEVEL`之后调用。

返回任何值都不会影响后续回调的执行。

???- example "Example Code"

    ```lua
    local function onStart(_,bool)
     print(bool)
    end
    mod:AddCallback(ModCallbacks.MC_POST_GAME_STARTED, onStart)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[ ](#){: .alldlc .tooltip .badge }|15 |MC_POST_GAME_STARTED {: .copyable } | (IsContinued [bool]) | - | void |

### MC_POST_GAME_END {: .copyable }

当游戏结束屏幕出现或结局开始播放时调用此函数。当您死亡并出现游戏结束时，布尔值为`true`；当您获胜并出现结局时，布尔值为`false`。

返回任何值都不会影响后续回调的执行。


???- example "Example Code"

    ```lua
    local function onEnd(_,bool)
        print(bool)
    end
    mod:AddCallback(ModCallbacks.MC_POST_GAME_END, onEnd)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[ ](#){: .alldlc .tooltip .badge }|16 |MC_POST_GAME_END {: .copyable } | (IsGameOver [bool]) | - | void |

### MC_PRE_GAME_EXIT {: .copyable }

当您退出游戏时调用此函数。当游戏通常会创建一个可继续的存档时，布尔值为`true`；当不会时，布尔值为`false`。当游戏播放结局时，会调用两次。

返回任何值都不会影响后续回调的执行。

???- example "Example Code"

    ```lua
    local function onExit(_,bool)
        print(bool)
    end
    mod:AddCallback(ModCallbacks.MC_PRE_GAME_EXIT, onExit)
    ```


|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[ ](#){: .alldlc .tooltip .badge }|17 |MC_PRE_GAME_EXIT {: .copyable } | (ShouldSave [bool]) | - | void |

### MC_POST_NEW_LEVEL {: .copyable }
在过渡到新关卡或阶段后触发。

不直观的是，它总是在`MC_POST_NEW_ROOM`之后调用。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[ ](#){: .alldlc .tooltip .badge }|18 |MC_POST_NEW_LEVEL {: .copyable } | -  | - | void |

### MC_POST_NEW_ROOM {: .copyable }
在进入房间后触发。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[ ](#){: .alldlc .tooltip .badge }|19 |MC_POST_NEW_ROOM {: .copyable } | -  | - | void |

### MC_GET_CARD {: .copyable }
此回调用于处理卡牌池。

由于并非所有卡牌都有相同的生成几率，因此使用[RNG](../RNG.md)进行种子随机选择。

您可以使用布尔值作为选择的过滤器。

返回值决定将生成什么[Card](Card.md)。返回`nil`以不替换生成的卡牌。

返回的值不会更新后续执行回调的“[Card](Card.md)”参数。

`IncludePlayingCards`参数决定是否包括类型为`ItemConfigCardType.SUIT`的卡牌。（这是通过查看任天堂Switch版本文件中的LuaJIT API代码确认的。）

???+ bug

    返回非整数或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[ ](#){: .alldlc .tooltip .badge }|20 |MC_GET_CARD {: .copyable } | ([RNG](../RNG.md),<br>[Card](Card.md),<br>IncludePlayingCards [bool],<br>IncludeRunes [bool],<br>OnlyRunes [bool]) | - | [Card](Card.md) |

### MC_GET_SHADER_PARAMS {: .copyable }
返回一个包含自定义着色器参数的键值对的表。

返回表时将跳过其余回调。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[ ](#){: .alldlc .tooltip .badge }|21 |MC_GET_SHADER_PARAMS {: .copyable } | (ShaderName [string]) | - | table |

### MC_EXECUTE_CMD {: .copyable }
返回一个用`<br />`（换行符）分隔的字符串，每行对应控制台输出。`CMD`是控制台输入的第一个单词。

参数是输入的其余部分。

???+ info "重要"

    此函数不会为默认游戏命令（如`Spawn`或`Debug`）调用。

返回字符串将其打印到控制台。

返回任何值都不会影响后续回调的执行。

???+ bug

    返回除`nil`以外的任何值将导致游戏崩溃，包括字符串。

???- example "Example Code"

    ```lua
    function mod.oncmd(_, command, args)
        print(command)
        print(args)
    end
    mod:AddCallback(ModCallbacks.MC_EXECUTE_CMD, mod.oncmd)
    -- executing command "Test apple 1 Pear test" prints
    -- Test
    -- apple 1 Pear test
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|22 |MC_EXECUTE_CMD {: .copyable } | (CMD [string],<br>Parameters [string]) | - | string |

### MC_PRE_USE_ITEM {: .copyable }

在使用道具之前调用。

返回`true`以阻止道具的默认代码触发。这仍会消耗道具的充能。

???+ bug

    返回除`nil`以外的任何值也将阻止后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|23 |MC_PRE_USE_ITEM {: .copyable } | ([CollectibleType](CollectibleType.md),<br>[RNG](../RNG.md),<br>[EntityPlayer](../EntityPlayer.md),<br>[UseFlags](UseFlag.md) [int],<br>[ActiveSlot](ActiveSlot.md),<br>CustomVarData [int])|[CollectibleType](CollectibleType.md) | boolean |

### MC_PRE_ENTITY_SPAWN {: .copyable }

在实体生成之前立即调用。

可选：返回一个包含新值`{ Type, Variant, Subtype, Seed }`的表，以覆盖生成实体的这些值。

如果您想阻止实体生成，不能返回`EntityType`为0，因为这会导致游戏崩溃。

有时，如果返回的类型与原始类型不同（例如，将拾取物替换为效果），游戏会崩溃。因此，您应该将拾取物替换为新的拾取物，依此类推。

???+ bug

    返回非表或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|24 |MC_PRE_ENTITY_SPAWN {: .copyable } | ([EntityType](EntityType.md),<br>Variant [int],<br>SubType [int],<br>Position [Vector],<br>Velocity [Vector],<br>Spawner [[Entity](../Entity.md)],<br>Seed [int]) | - | table |

### MC_POST_FAMILIAR_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|25 |MC_POST_FAMILIAR_RENDER {: .copyable } | ([EntityFamiliar](../EntityFamiliar.md),<br>RenderOffset [Vector])|[FamiliarVariant](FamiliarVariant.md) | void |

### MC_PRE_FAMILIAR_COLLISION {: .copyable }

当实体首先与碰撞器碰撞时，`Low`值为`true`。如果碰撞器首先碰撞，则为`false`。

返回`true`以忽略碰撞，返回`false`以进行碰撞但不执行内部代码，返回`nil`以继续执行内部代码（例如，接触时受到伤害）。
返回任何非`nil`值将跳过其余回调。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|26 |MC_PRE_FAMILIAR_COLLISION {: .copyable } | ([EntityFamiliar](../EntityFamiliar.md),<br>Collider [[Entity](../Entity.md)],<br>Low [bool])|[FamiliarVariant](FamiliarVariant.md) | boolean |

### MC_POST_NPC_INIT {: .copyable }

返回任何值都不会影响后续回调的执行。

???- warning "警告"
    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_NPC_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|27 |MC_POST_NPC_INIT {: .copyable } | ([EntityNPC](../EntityNPC.md))|[EntityType](EntityType.md) | void |

### MC_POST_NPC_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|28 |MC_POST_NPC_RENDER {: .copyable } | ([EntityNPC](../EntityNPC.md),<br>RenderOffset [Vector])|[EntityType](EntityType.md) | void |

### MC_POST_NPC_DEATH {: .copyable }

在死亡动画播放后调用。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|29 |MC_POST_NPC_DEATH {: .copyable } | ([EntityNPC](../EntityNPC.md))|[EntityType](EntityType.md) | void |

### MC_PRE_NPC_COLLISION {: .copyable }

当实体首先与碰撞器碰撞时，`Low`值为`true`。如果碰撞器首先碰撞，则为`false`。

返回`true`以忽略碰撞，返回`false`以进行碰撞但不执行内部代码，返回`nil`以继续执行内部代码（例如，接触时受到伤害）。
返回任何非`nil`值将跳过其余回调。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|30 |MC_PRE_NPC_COLLISION {: .copyable } | ([EntityNPC](../EntityNPC.md),<br>Collider [[Entity](../Entity.md)],<br>Low [bool])|[EntityType](EntityType.md) | boolean |

### MC_POST_PLAYER_UPDATE {: .copyable }

可选参数可用于指定玩家变体。0 = 玩家，1 = 合作宝宝。

返回任何值都不会影响后续回调的执行。

???- info "执行信息"
    此回调每秒调用60次。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|31 |MC_POST_PLAYER_UPDATE {: .copyable } | ([EntityPlayer](../EntityPlayer.md))|PlayerVariant* | void |

### MC_POST_PLAYER_RENDER {: .copyable }

可选参数可用于指定玩家变体。0 = 玩家，1 = 合作宝宝。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|32 |MC_POST_PLAYER_RENDER {: .copyable } | ([EntityPlayer](../EntityPlayer.md),<br>RenderOffset [Vector])|PlayerVariant* | void |

### MC_PRE_PLAYER_COLLISION {: .copyable }

当实体首先与碰撞器碰撞时，`Low`值为`true`。如果碰撞器首先碰撞，则为`false`。

返回`true`以忽略碰撞，返回`false`以进行碰撞但不执行内部代码，返回`nil`以继续执行内部代码（例如，接触时受到伤害）。
返回任何非`nil`值将跳过其余回调。

可选参数可用于指定玩家变体。0 = 玩家，1 = 合作宝宝。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|33 |MC_PRE_PLAYER_COLLISION {: .copyable } | ([EntityPlayer](../EntityPlayer.md),<br>Collider [[Entity](../Entity.md)],<br>Low [bool])|PlayerVariant* | boolean |

### MC_POST_PICKUP_INIT {: .copyable }

返回任何值都不会影响后续回调的执行。

???- warning "警告"

    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_PICKUP_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|34 |MC_POST_PICKUP_INIT {: .copyable } | ([EntityPickup](../EntityPickup.md))|[PickupVariant](PickupVariant.md) | void |

### MC_POST_PICKUP_UPDATE {: .copyable }

返回任何值都不会影响后续回调的执行。

???- info "执行信息"

    此回调将在实体存在的第1帧调用。只有当您进入一个已经包含生成的拾取物的房间时，才会在第0帧调用。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|35 |MC_POST_PICKUP_UPDATE {: .copyable } | ([EntityPickup](../EntityPickup.md))|[PickupVariant](PickupVariant.md) | void |

### MC_POST_PICKUP_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|36 |MC_POST_PICKUP_RENDER {: .copyable } | ([EntityPickup](../EntityPickup.md),<br>RenderOffset [Vector])|[PickupVariant](PickupVariant.md) | void |

### MC_POST_PICKUP_SELECTION {: .copyable }

在从随机拾取物列表中选择一个拾取物进行生成后调用。返回`nil`以继续执行默认游戏代码。

返回一个表`{ Variant, Subtype }`以覆盖指定的值。这也会影响后续执行的回调。

???+ bug

    返回非表或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

???+ bug

    [EntityPickup](../EntityPickup.md)包含要生成的拾取物的类型/变体，但在其他方面是一个空类，值为空或为零。

    当进入一个包含已经选择的拾取物的房间时，也会调用此回调。当玩家丢弃一张卡牌时，也会调用此回调。这些事实使得此回调对于处理拾取物池没有用处。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|37 |MC_POST_PICKUP_SELECTION {: .copyable } | ([EntityPickup](../EntityPickup.md),<br>Variant [int],<br>Subtype [int]) | - | table |

### MC_PRE_PICKUP_COLLISION {: .copyable }

当实体首先与碰撞器碰撞时，`Low`值为`true`。如果碰撞器首先碰撞，则为`false`。

返回`true`以忽略碰撞，返回`false`以进行碰撞但不执行内部代码，返回`nil`以继续执行内部代码（例如，接触时受到伤害）。
返回任何非`nil`值将跳过其余回调。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|38 |MC_PRE_PICKUP_COLLISION {: .copyable } | ([EntityPickup](../EntityPickup.md),<br>Collider [[Entity](../Entity.md)],<br>Low [bool])|[PickupVariant](PickupVariant.md) | boolean |

### MC_POST_TEAR_INIT {: .copyable }

返回任何值都不会影响后续回调的执行。

???- warning "警告"

    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_TEAR_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|39 |MC_POST_TEAR_INIT {: .copyable } | ([EntityTear](../EntityTear.md))|[TearVariant](TearVariant.md) | void |

### MC_POST_TEAR_UPDATE {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|40 |MC_POST_TEAR_UPDATE {: .copyable } | ([EntityTear](../EntityTear.md))|[TearVariant](TearVariant.md) | void |

### MC_POST_TEAR_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|41 |MC_POST_TEAR_RENDER {: .copyable } | ([EntityTear](../EntityTear.md),<br>RenderOffset [Vector])|[TearVariant](TearVariant.md) | void |

### MC_PRE_TEAR_COLLISION {: .copyable }

当实体首先与碰撞器碰撞时，`Low`值为`true`。如果碰撞器首先碰撞，则为`false`。

返回`true`以忽略碰撞，返回`false`以进行碰撞但不执行内部代码，返回`nil`以继续执行内部代码（例如，接触时受到伤害）。
返回任何非`nil`值将跳过其余回调。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|42 |MC_PRE_TEAR_COLLISION {: .copyable } | ([EntityTear](../EntityTear.md),<br>Collider [[Entity](../Entity.md)],<br>Low [bool])|[TearVariant](TearVariant.md) | boolean |

### MC_POST_PROJECTILE_INIT {: .copyable }

返回任何值都不会影响后续回调的执行。

???- warning "警告"
    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_PROJECTILE_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|43 |MC_POST_PROJECTILE_INIT {: .copyable } | ([EntityProjectile](../EntityProjectile.md))|[ProjectileVariant](ProjectileVariant.md) | void |

### MC_POST_PROJECTILE_UPDATE {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|44 |MC_POST_PROJECTILE_UPDATE {: .copyable } | ([EntityProjectile](../EntityProjectile.md))|[ProjectileVariant](ProjectileVariant.md) | void |

### MC_POST_PROJECTILE_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|45 |MC_POST_PROJECTILE_RENDER {: .copyable } | ([EntityProjectile](../EntityProjectile.md),<br>RenderOffset [Vector])|[ProjectileVariant](ProjectileVariant.md) | void |

### MC_PRE_PROJECTILE_COLLISION {: .copyable }

当实体首先与碰撞器碰撞时，`Low`值为`true`。如果碰撞器首先碰撞，则为`false`。

返回`true`以忽略碰撞，返回`false`以进行碰撞但不执行内部代码，返回`nil`以继续执行内部代码（例如，接触时受到伤害）。
返回任何非`nil`值将跳过其余回调。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|46 |MC_PRE_PROJECTILE_COLLISION {: .copyable } | ([EntityProjectile](../EntityProjectile.md),<br>Collider [[Entity](../Entity.md)],<br>Low [bool])|[ProjectileVariant](ProjectileVariant.md) | boolean |

### MC_POST_LASER_INIT {: .copyable }

返回任何值都不会影响后续回调的执行。

???- warning "警告"

    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_LASER_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|47 |MC_POST_LASER_INIT {: .copyable } | ([EntityLaser](../EntityLaser.md))|LaserVariant | void |

### MC_POST_LASER_UPDATE {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|48 |MC_POST_LASER_UPDATE {: .copyable } | ([EntityLaser](../EntityLaser.md))|LaserVariant | void |

### MC_POST_LASER_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|49 |MC_POST_LASER_RENDER {: .copyable } | ([EntityLaser](../EntityLaser.md),<br>RenderOffset [Vector])|LaserVariant | void |

### MC_POST_KNIFE_INIT {: .copyable }

返回任何值都不会影响后续回调的执行。

???+ note

    可选参数是一个子类型，**不是**变体！

???- warning "警告"

    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_KNIFE_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|50 |MC_POST_KNIFE_INIT {: .copyable } | ([EntityKnife](../EntityKnife.md))|KnifeSubType * | void |

### MC_POST_KNIFE_UPDATE {: .copyable }

返回任何值都不会影响后续回调的执行。

???+ note

    可选参数是一个子类型，**不是**变体！

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|51 |MC_POST_KNIFE_UPDATE {: .copyable } | ([EntityKnife](../EntityKnife.md))|KnifeSubType * | void |

### MC_POST_KNIFE_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

???+ note

    可选参数是一个子类型，**不是**变体！

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|52 |MC_POST_KNIFE_RENDER {: .copyable } | ([EntityKnife](../EntityKnife.md),<br>RenderOffset [Vector])|KnifeSubType * | void |

### MC_PRE_KNIFE_COLLISION {: .copyable }

当实体首先与碰撞器碰撞时，`Low`值为`true`。如果碰撞器首先碰撞，则为`false`。

返回`true`以忽略碰撞，返回`false`以进行碰撞但不执行内部代码，返回`nil`以继续执行内部代码（例如，接触时受到伤害）。
返回任何非`nil`值将跳过其余回调。

???+ note

    可选参数是一个子类型，**不是**变体！

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|53 |MC_PRE_KNIFE_COLLISION {: .copyable } | ([EntityKnife](../EntityKnife.md),<br>Collider [[Entity](../Entity.md)],<br>Low [bool])|KnifeSubType * | boolean |

### MC_POST_EFFECT_INIT {: .copyable }

返回任何值都不会影响后续回调的执行。

???- warning "警告"

    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_EFFECT_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|54 |MC_POST_EFFECT_INIT {: .copyable } | ([EntityEffect](../EntityEffect.md))|[EffectVariant](EffectVariant.md) | void |

### MC_POST_EFFECT_UPDATE {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|55 |MC_POST_EFFECT_UPDATE {: .copyable } | ([EntityEffect](../EntityEffect.md))|[EffectVariant](EffectVariant.md) | void |

### MC_POST_EFFECT_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|56 |MC_POST_EFFECT_RENDER {: .copyable } | ([EntityEffect](../EntityEffect.md),<br>RenderOffset [Vector])|[EffectVariant](EffectVariant.md) | void |

### MC_POST_BOMB_INIT {: .copyable }

返回任何值都不会影响后续回调的执行。

???- warning "警告"

    在某些用例中，访问初始化的实体提供的数据是不完整的。在`PostInit`回调调用之前，只有`Position`、`Velocity`、`SpawnerType`、`SpawnerVariant`、`SpawnerEntity`等一些属性被设置，因此可以访问。其他一些属性（例如效果属性或眼泪标志）将不会被设置。如果您想访问这些值，您需要挂钩到`MC_POST_BOMB_UPDATE`并在第一帧检查这些属性。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|57 |MC_POST_BOMB_INIT {: .copyable } | ([EntityBomb](../EntityBomb.md))|[BombVariant](BombVariant.md) | void |

### MC_POST_BOMB_UPDATE {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|58 |MC_POST_BOMB_UPDATE {: .copyable } | ([EntityBomb](../EntityBomb.md))|[BombVariant](BombVariant.md) | void |

### MC_POST_BOMB_RENDER {: .copyable }

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|59 |MC_POST_BOMB_RENDER {: .copyable } | ([EntityBomb](../EntityBomb.md),<br>Offset [Vector])|[BombVariant](BombVariant.md) | void |

### MC_PRE_BOMB_COLLISION {: .copyable }

当实体首先与碰撞器碰撞时，`Low`值为`true`。如果碰撞器首先碰撞，则为`false`。

返回`true`以忽略碰撞，返回`false`以进行碰撞但不执行内部代码，返回`nil`以继续执行内部代码（例如，接触时受到伤害）。
返回任何非`nil`值将跳过其余回调。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|60 |MC_PRE_BOMB_COLLISION {: .copyable } | ([EntityBomb](../EntityBomb.md),<br>Collider [[Entity](../Entity.md)],<br>Low [bool])|[BombVariant](BombVariant.md) | boolean |

### MC_POST_FIRE_TEAR {: .copyable }

当玩家发射眼泪时调用。

返回任何值都不会影响后续回调的执行。

对于重生+，对于其他武器或用孵化器发射的眼泪，此回调不会调用。在忏悔中，它适用于用孵化器发射的眼泪。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|61 |MC_POST_FIRE_TEAR {: .copyable } | ([EntityTear](../EntityTear.md)) | - | void |

### MC_PRE_GET_COLLECTIBLE {: .copyable }

当游戏需要从道具池中获取一个新的随机道具时调用此回调。

您可以从此回调中返回一个整数，以更改返回的收集品类型。

它不会为“脚本化”掉落（如愤怒的炸弹先生）和手动生成的道具调用。

返回的值不会改变后续执行回调的参数。

返回任何非`nil`值将导致**MC_POST_GET_COLLECTIBLE**被跳过。

???+ bug

    返回非表或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

???- info "注意事项"

    **ItemPoolType**始终指的是原始请求的道具池，无论混沌是否干扰了道具池。但是，您可以通过检查[ItemPool::GetLastPool()](../ItemPool.md#getlastpool)返回的内容来了解实际将使用哪个道具池。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|62 |MC_PRE_GET_COLLECTIBLE {: .copyable } | ([ItemPoolType](ItemPoolType.md),<br>Decrease [bool],<br>Seed [int]) | - | int |

### MC_POST_GET_COLLECTIBLE {: .copyable }

此函数在`MC_PRE_GET_COLLECTIBLE`之后立即调用，并确定将从给定的[ItemPoolType](ItemPoolType.md)中生成的收集品。

如果`MC_PRE_GET_COLLECTIBLE`返回了任何非`nil`值，则此回调将被跳过。

您可以从此回调中返回一个整数，以更改返回的收集品类型。

返回的值不会更新后续执行回调的“SelectedCollectible”参数。

???- info "注意事项"

    **ItemPoolType**始终指的是原始请求的道具池，无论混沌是否干扰了道具池。但是，您可以通过检查[ItemPool::GetLastPool()](../ItemPool.md#getlastpool)返回的内容来了解实际使用了哪个道具池。

???+ bug

    返回非表或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|63 |MC_POST_GET_COLLECTIBLE {: .copyable } | (SelectedCollectible [[CollectibleType](CollectibleType.md)],<br>[ItemPoolType](ItemPoolType.md),<br>Decrease [bool],<br>Seed [int]) | - | table |

### MC_GET_PILL_COLOR {: .copyable }

当游戏生成药丸并需要确定其药丸颜色时调用此函数。

返回一个`PillColor`以指定需要选择的药丸颜色。不返回任何值则让游戏处理。

返回的值不会改变后续执行回调的参数。

???+ bug

    返回非表或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|64 |MC_GET_PILL_COLOR {: .copyable } | (Seed [int]) | - | [PillColor](PillColor.md) |

### MC_GET_PILL_EFFECT {: .copyable }

游戏获取药丸的[PillEffect](PillEffect.md)时每帧调用。可以通过返回所选的[PillEffect](PillEffect.md)来选择药丸的效果。

该效果将应用于相同药丸颜色的所有药丸，而不是单个药丸。

返回的值不会更新后续执行回调的“SelectedPillEffect”参数。

???+ bug

    返回非表或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

???- example "Example Code"

This code turn "Bad Trip" pills into "Balls of Steel" pills.

    ```lua
    function mod:getPillEffect(pillEffect, pillColor)
        if pillEffect == PillEffect.PILLEFFECT_BAD_TRIP then
        return PillEffect.PILLEFFECT_BALLS_OF_STEEL
        end
    end
    mod:AddCallback(ModCallbacks.MC_GET_PILL_EFFECT, mod.getPillEffect)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|65 |MC_GET_PILL_EFFECT {: .copyable } | (SelectedPillEffect [[PillEffect](PillEffect.md)],<br>PillColor) | - | table |

### MC_GET_TRINKET {: .copyable }

当需要确定饰品的[TrinketType](TrinketType.md)时调用。

可以返回一个[TrinketType](TrinketType.md)以更改所选的饰品。

返回的值不会更新后续执行回调的“SelectedTrinket”参数。

???+ bug

    返回非表或`nil`的值将导致游戏崩溃。

???+ warning "警告"

    最后一个返回有效返回值的回调将胜出并覆盖先前回调的返回值。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|66 |MC_GET_TRINKET {: .copyable } | (SelectedTrinket [[TrinketType](TrinketType.md)],<br>[RNG](../RNG.md)) | - | table |

### MC_POST_ENTITY_REMOVE {: .copyable }

每当游戏移除一个[Entity](../Entity.md)时调用。这包括死亡、击杀、移除，甚至在房间过渡时卸载实体或结束游戏。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|67 |MC_POST_ENTITY_REMOVE {: .copyable } | ([Entity](../Entity.md))|[EntityType](EntityType.md) | void |

### MC_POST_ENTITY_KILL {: .copyable }

在[Entity](../Entity.md)的死亡动画触发之前立即调用。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|68 |MC_POST_ENTITY_KILL {: .copyable } | ([Entity](../Entity.md))|[EntityType](EntityType.md) | void |

### MC_PRE_NPC_UPDATE {: .copyable }

如果应忽略NPC的内部AI，则返回`true`，否则返回`nil`/不返回任何值。返回任何非`nil`值将跳过其余回调。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|69 |MC_PRE_NPC_UPDATE {: .copyable } | ([EntityNPC](../EntityNPC.md)) |[EntityType](EntityType.md) | boolean |

### MC_PRE_SPAWN_CLEAN_AWARD {: .copyable }

此函数在每个可以清空的房间中触发，包括BOSS和天使房间，甚至在通常不会生成奖励的情况下也会触发。

此回调还处理特殊生成，例如BOSS被击杀后的活板门、为当前角色授予完成标记，以及在某些情况下结束游戏（妈妈、超级撒旦和野兽）。因此，在此返回`true`也将取消这些事件。

如果应忽略生成例程，则返回`true`，否则返回`nil`/不返回任何值。返回任何非`nil`值将跳过其余回调。

???+ bug

    返回`true`将导致房间的奖励种子不前进，导致在同一房间中后续调用此回调时具有相同的RNG对象。要修复此问题，您可以使用以下代码片段手动更新奖励种子。

    ```lua
    function mod:preSpawnCleanAward(rng)
        local level = Game():GetLevel()
        local roomDesc = level:GetRoomDesc(level:GetCurrentRoomIndex())
        roomDesc.AwardSeed = rng:GetSeed()
        return true
    end
    mod:AddCallback(ModCallbacks.MC_PRE_SPAWN_CLEAN_AWARD, mod.preSpawnCleanAward)
    ```

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|70 |MC_PRE_SPAWN_CLEAN_AWARD {: .copyable } | ([RNG](../RNG.md),<br>SpawnPosition [Vector]) | - | boolean |

### MC_PRE_ROOM_ENTITY_SPAWN {: .copyable }

在进入新房间时，在生成作为房间布局一部分的实体之前调用。网格实体也会触发此回调，并且它们的类型将与`gridspawn`命令使用的类型相同。因此，在此回调中，效果被分配类型999而不是1000。

可选：返回一个包含新值`{ Type, Variant, Subtype }`的表。返回这样的表将覆盖可能自然发生的任何替换，例如敌人变体。

返回任何值都不会影响后续回调的执行。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .alldlc .tooltip .badge }|71 |MC_PRE_ROOM_ENTITY_SPAWN {: .copyable } | ([EntityType](EntityType.md),<br>Variant [int],<br>SubType [int],<br>GridIndex [int],<br>Seed [int]) | - | table |

### MC_PRE_ENTITY_DEVOLVE {: .copyable }

当实体通过D10或类似物品退化时调用。

如果应忽略内部退化行为，则返回`true` - 当返回`true`时，此回调负责生成退化后的实体并移除原始实体。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .reporplus .tooltip .badge }|72 |MC_PRE_ENTITY_DEVOLVE {: .copyable } | ([Entity](../Entity.md)) | - | boolean |

### MC_PRE_MOD_UNLOAD {: .copyable }

在任何模组卸载之前（禁用模组或使用`luamod`重新加载模组时）调用，模组的表作为参数传递。

|DLC|Value|Name|Function Args|Optional Args|Return Type|
|:--|:--|:--|:--|:--|:--|
|[](#){: .reporplus .tooltip .badge }|73 |MC_PRE_MOD_UNLOAD {: .copyable } | table Mod | - | void |
