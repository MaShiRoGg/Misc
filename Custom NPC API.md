<!-- vscode-markdown-toc -->
* 1. [npc](#npc)
	* 1.1. [attack](#attack)
	* 1.2. [damaged](#damaged)
	* 1.3. [died](#died)
	* 1.4. [init](#init)
	* 1.5. [interact](#interact)
	* 1.6. [kill](#kill)
	* 1.7. [meleeAttack](#meleeAttack)
	* 1.8. [rangedAttack](#rangedAttack)
	* 1.9. [target](#target)
	* 1.10. [targetLost](#targetLost)
	* 1.11. [timer](#timer)
	* 1.12. [tick](#tick)
* 2. [player](#player)
	* 2.1. [attack](#attack-1)
	* 2.2. [broken](#broken)
	* 2.3. [chat](#chat)
	* 2.4. [containerClosed](#containerClosed)
	* 2.5. [containerOpen](#containerOpen)
	* 2.6. [damaged](#damaged-1)
	* 2.7. [died](#died-1)
	* 2.8. [factionUpdate](#factionUpdate)
	* 2.9. [init](#init-1)
	* 2.10. [interact](#interact-1)
	* 2.11. [keyPressed](#keyPressed)
	* 2.12. [kill](#kill-1)
	* 2.13. [levelUp](#levelUp)
	* 2.14. [login](#login)
	* 2.15. [logout](#logout)
	* 2.16. [pickedUp](#pickedUp)
	* 2.17. [rangedLaunched](#rangedLaunched)
	* 2.18. [timer](#timer-1)
	* 2.19. [toss](#toss)
	* 2.20. [tick](#tick-1)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->Custom Npc API 的使用

[Custom Npc API官方文档](https://www.kodevelopment.nl/customnpcs/api/1.12.2/) 英文



# 钩子函数

使用方法举例：
```python
def attack(c):
    pass # 检测到攻击事件后执行的代码

def damaged(c):
    pass # 检测到受伤事件后执行的代码
```
##  1. <a name='npc'></a>npc
共有参数解析:  
`c.npc` 关于npc本身的一些API方法(ICustomNpc)   
`c.API` 一些基础API方法(NpcAPI)   

###  1.1. <a name='attack'></a>attack
当npc进行攻击时触发  

特殊参数解析:  
`c.damage` 本次攻击的伤害(float)  
`c.target` 被攻击的对象(IEntityLivingBase)  

###  1.2. <a name='damaged'></a>damaged
当npc受伤时触发  

特殊参数解析:  
`c.clearTarget` 暂时未知  
`c.damage`  受到的伤害(float)  
`c.damageSource`  伤害的来源(IDamageSource)  
`c.source` 伤害的来源对象(IEntity)  

###  1.3. <a name='died'></a>died
当npc死亡时触发  

特殊参数解析:  
`c.line` 暂时未知(ILine)  
`c.droppedItems`  死亡掉落的物品(IItemStack[])  
`c.damageSource`  死亡的来源(IDamageSource)  
`c.source` 死亡的来源对象(IEntity)  
`c.expDropped` 掉落的经验值(int)  

###  1.4. <a name='init'></a>init
当npc初始化时触发  

###  1.5. <a name='interact'></a>interact
当与npc交互时触发  

特殊参数解析:  
`c.player` 与npc交互的玩家(IPlayer)  

###  1.6. <a name='kill'></a>kill
当npc杀死实体时触发  

特殊参数解析:  

`c.entity` 杀死的实体(IEntityLivingBase)

###  1.7. <a name='meleeAttack'></a>meleeAttack
当npc进行近战攻击时触发  

特殊参数解析:  

`c.damage` 本次攻击的伤害(float)  
`c.target` 被攻击的对象(IEntityLivingBase)  

###  1.8. <a name='rangedAttack'></a>rangedAttack
当npc进行远程攻击时触发  

特殊参数解析:  

`c.damage` 本次攻击的伤害(float)  
`c.projectiles` 本次攻击的发射物(java.util.List\<IProjectile\>)  
`c.target` 被攻击的对象(IEntityLivingBase)  

###  1.9. <a name='target'></a>target
当npc发现敌对实体时触发  

特殊参数解析:   

`c.entity` 敌对的实体(IEntityLivingBase)  

###  1.10. <a name='targetLost'></a>targetLost
当npc敌对实体死亡时触发  

特殊参数解析:  

`c.entity` 敌对实体的死亡之前的实体(IEntityLivingBase)  

###  1.11. <a name='timer'></a>timer
当关于npc的脚本中定时器触发时触发

特殊参数解析:  
 
`c.id` 定时器的id(int)  

###  1.12. <a name='tick'></a>tick
每0.5秒触发一次


##  2. <a name='player'></a>player

共有参数解析:  
`c.player` 关于player本身的一些API方法(IPlayer)   
`c.API` 一些基础API方法(NpcAPI)  

###  2.1. <a name='attack-1'></a>attack
玩家鼠标左键点击时触发

特殊参数解析:  
`c.target` 玩家左键点击的对象(java.lang.Object)  
`c.type` 对象类型(int)  
0: 空气 1:实体 2:方块


###  2.2. <a name='broken'></a>broken
玩家破坏方块时触发

特殊参数解析:  
`c.block` 玩家破坏的方块(IBlock)  
`c.exp` 破坏方块掉落的经验(int)  

###  2.3. <a name='chat'></a>chat
玩家在聊天栏说话时触发

特殊参数解析:  
`c.message` 聊天内容(java.lang.String)   

###  2.4. <a name='containerClosed'></a>containerClosed
玩家物品栏/容器关闭时触发

特殊参数解析:  
`c.container` 容器对象(IContainer)   

###  2.5. <a name='containerOpen'></a>containerOpen
玩家物品栏/容器打开时触发

特殊参数解析:  
`c.container` 容器对象(IContainer)   

###  2.6. <a name='damaged-1'></a>damaged
当玩家受伤时触发  

特殊参数解析:  
`c.damage`  受到的伤害(float)  
`c.damageSource`  伤害的来源(IDamageSource)  
`c.source` 伤害的来源对象(IEntity)  

###  2.7. <a name='died-1'></a>died
玩家死亡时触发

特殊参数解析:  
`c.damageSource`  造成死亡的来源(IDamageSource)  
`c.source` 造成死亡的来源对象(IEntity)  
`c.type` 造成死亡的类型描述(java.lang.String)

###  2.8. <a name='factionUpdate'></a>factionUpdate
玩家阵营点数发生变动时触发

特殊参数解析:  
`c.faction` 阵营(IFaction)  
`c.init` 是否默认对玩家设置了阵营点数(boolean)  
`c.points` 当前阵营点数(int)  


###  2.9. <a name='init-1'></a>init
当player初始化时触发  

###  2.10. <a name='interact-1'></a>interact
鼠标右键按下触发  

特殊参数解析:  
`c.target` 右键的对象(java.lang.Object)  
`c.type` 右键对象的类型(int)  
0:空气 1:实体 2:方块  

###  2.11. <a name='keyPressed'></a>keyPressed
键盘按下触发

特殊参数解析:  
`c.isAltPressed` 是否Alt键按下(boolean)  
`c.isCtrlPressed` 是否Ctrl键按下(boolean)  
`c.isMetaPressed` 是否Windows键按下(boolean)   
`c.isShiftPressed` 是否Shift键按下(boolean) 
`c.key` 按键值(int)  
[按键对照官方英文网址](https://minecraft.fandom.com/wiki/Key_codes)  
[按键对照官方中文网址](https://zh.minecraft.wiki/w/%E9%94%AE%E6%8E%A7%E4%BB%A3%E7%A0%81)


###  2.12. <a name='kill-1'></a>kill
当玩家杀死实体时触发  

特殊参数解析:  

`c.entity` 杀死的实体(IEntityLivingBase)

###  2.13. <a name='levelUp'></a>levelUp
当玩家升级时触发

特殊参数解析:

`c.change` 等级改变值(int)  

###  2.14. <a name='login'></a>login
玩家登入时触发

###  2.15. <a name='logout'></a>logout
玩家退出时触发

###  2.16. <a name='pickedUp'></a>pickedUp
玩家拾取一种物品时触发

特殊参数解析:
`c.item` 拾取的物品(IItemStack)

###  2.17. <a name='rangedLaunched'></a>rangedLaunched
暂时未知

###  2.18. <a name='timer-1'></a>timer
当关于玩家的脚本中定时器触发时触发

特殊参数解析:  
 
`c.id` 定时器的id(int)  

###  2.19. <a name='toss'></a>toss
玩家丢弃一种物品时触发

特殊参数解析:
`c.item` 丢弃的物品(IItemStack)

###  2.20. <a name='tick-1'></a>tick
每0.5秒触发一次
