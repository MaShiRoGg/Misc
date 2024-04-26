Custom Npc API 的使用

[Custom Npc API官方文档](https://www.kodevelopment.nl/customnpcs/api/1.12.2/) 英文

# 钩子函数

使用方法举例：
```python
def attack(c):
    pass # 检测到攻击事件后执行的代码

def damaged(c):
    pass # 检测到受伤事件后执行的代码
```
## npc
共有参数解析:  
`c.npc` 关于npc本身的一些API方法(ICustomNpc)   
`c.API` 一些基础API方法(NpcAPI)   

### attack
当npc进行攻击时触发  

特殊参数解析:  
`c.damage` 本次攻击的伤害(float)  
`c.target` 被攻击的对象(IEntityLivingBase)  

### damaged
当npc受伤时触发  

特殊参数解析:  
`c.clearTarget` 暂时未知  
`c.damage`  受到的伤害(float)  
`c.damageSource`  伤害的来源(IDamageSource)  
`c.source` 伤害的来源对象(IEntity)  

### died
当npc死亡时触发  

特殊参数解析:  
`c.line` 暂时未知(ILine)  
`c.droppedItems`  死亡掉落的物品(IItemStack[])  
`c.damageSource`  死亡的来源(IDamageSource)  
`c.source` 死亡的来源对象(IEntity)  
`c.expDropped` 掉落的经验值(int)  

### init
当npc初始化时触发  

### interact
当与npc交互时触发  

特殊参数解析:  
`c.player` 与npc交互的玩家(IPlayer)  

### kill
当npc杀死实体时触发  

特殊参数解析:  

`c.entity` 杀死的实体(IEntityLivingBase)

### meleeAttack
当npc进行近战攻击时触发  

特殊参数解析:  

`c.damage` 本次攻击的伤害(float)  
`c.target` 被攻击的对象(IEntityLivingBase)  

### rangedAttack
当npc进行远程攻击时触发  

特殊参数解析:  

`c.damage` 本次攻击的伤害(float)  
`c.projectiles` 本次攻击的发射物(java.util.List\<IProjectile\>)  
`c.target` 被攻击的对象(IEntityLivingBase)  

### target
当npc发现敌对实体时触发  

特殊参数解析:   

`c.entity` 敌对的实体(IEntityLivingBase)  

### targetLost
当npc敌对实体死亡时触发  

特殊参数解析:  

`c.entity` 敌对实体的死亡之前的实体(IEntityLivingBase)  

### timer
当关于npc的脚本中定时器触发时触发

特殊参数解析:  
 
`c.id` 定时器的id(int)  

### tick
每0.5秒触发一次


## player

共有参数解析:  
`c.player` 关于player本身的一些API方法(IPlayer)   
`c.API` 一些基础API方法(NpcAPI)  

### attack
玩家鼠标左键点击时触发

特殊参数解析:  
`c.target` 玩家左键点击的对象(java.lang.Object)  
`c.type` 对象类型(int)  
0: 空气 1:实体 2:方块


### broken
玩家破坏方块时触发

特殊参数解析:  
`c.block` 玩家破坏的方块(IBlock)  
`c.exp` 破坏方块掉落的经验(int)  

### chat
玩家在聊天栏说话时触发

特殊参数解析:  
`c.message` 聊天内容(java.lang.String)   

### containerClosed
玩家物品栏/容器关闭时触发

特殊参数解析:  
`c.container` 容器对象(IContainer)   

### containerOpen
玩家物品栏/容器打开时触发

特殊参数解析:  
`c.container` 容器对象(IContainer)   

### damaged
当玩家受伤时触发  

特殊参数解析:  
`c.damage`  受到的伤害(float)  
`c.damageSource`  伤害的来源(IDamageSource)  
`c.source` 伤害的来源对象(IEntity)  

### died
玩家死亡时触发

特殊参数解析:  
`c.damageSource`  造成死亡的来源(IDamageSource)  
`c.source` 造成死亡的来源对象(IEntity)  
`c.type` 造成死亡的类型描述(java.lang.String)

### factionUpdate
玩家阵营点数发生变动时触发

特殊参数解析:  
`c.faction` 阵营(IFaction)  
`c.init` 是否默认对玩家设置了阵营点数(boolean)  
`c.points` 当前阵营点数(int)  


### init
当player初始化时触发  

### interact
鼠标右键按下触发  

特殊参数解析:  
`c.target` 右键的对象(java.lang.Object)  
`c.type` 右键对象的类型(int)  
0:空气 1:实体 2:方块  

### keyPressed
键盘按下触发

特殊参数解析:  
`c.isAltPressed` 是否Alt键按下(boolean)  
`c.isCtrlPressed` 是否Ctrl键按下(boolean)  
`c.isMetaPressed` 是否Windows键按下(boolean)   
`c.isShiftPressed` 是否Shift键按下(boolean) 
`c.key` 按键值(int)  
[按键对照官方英文网址](https://minecraft.fandom.com/wiki/Key_codes)  
[按键对照官方中文网址](https://zh.minecraft.wiki/w/%E9%94%AE%E6%8E%A7%E4%BB%A3%E7%A0%81)


### kill
当玩家杀死实体时触发  

特殊参数解析:  

`c.entity` 杀死的实体(IEntityLivingBase)

### levelUp
当玩家升级时触发

特殊参数解析:

`c.change` 等级改变值(int)  

### login
玩家登入时触发

### logout
玩家退出时触发

### pickedUp
玩家拾取一种物品时触发

特殊参数解析:
`c.item` 拾取的物品(IItemStack)

### rangedLaunched
暂时未知

### timer
当关于玩家的脚本中定时器触发时触发

特殊参数解析:  
 
`c.id` 定时器的id(int)  

### toss
玩家丢弃一种物品时触发

特殊参数解析:
`c.item` 丢弃的物品(IItemStack)

### tick
每0.5秒触发一次
