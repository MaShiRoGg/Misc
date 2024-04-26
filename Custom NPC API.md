<!-- vscode-markdown-toc -->
* 1. [钩子函数](#)
	* 1.1. [npc](#npc)
		* 1.1.1. [attack](#attack)
		* 1.1.2. [damaged](#damaged)
		* 1.1.3. [died](#died)
		* 1.1.4. [init](#init)
		* 1.1.5. [interact](#interact)
		* 1.1.6. [kill](#kill)
		* 1.1.7. [meleeAttack](#meleeAttack)
		* 1.1.8. [rangedAttack](#rangedAttack)
		* 1.1.9. [target](#target)
		* 1.1.10. [targetLost](#targetLost)
		* 1.1.11. [timer](#timer)
		* 1.1.12. [tick](#tick)
	* 1.2. [player](#player)
		* 1.2.1. [attack](#attack-1)
		* 1.2.2. [broken](#broken)
		* 1.2.3. [chat](#chat)
		* 1.2.4. [containerClosed](#containerClosed)
		* 1.2.5. [containerOpen](#containerOpen)
		* 1.2.6. [damaged](#damaged-1)
		* 1.2.7. [died](#died-1)
		* 1.2.8. [factionUpdate](#factionUpdate)
		* 1.2.9. [init](#init-1)
		* 1.2.10. [interact](#interact-1)
		* 1.2.11. [keyPressed](#keyPressed)
		* 1.2.12. [kill](#kill-1)
		* 1.2.13. [levelUp](#levelUp)
		* 1.2.14. [login](#login)
		* 1.2.15. [logout](#logout)
		* 1.2.16. [pickedUp](#pickedUp)
		* 1.2.17. [rangedLaunched](#rangedLaunched)
		* 1.2.18. [timer](#timer-1)
		* 1.2.19. [toss](#toss)
		* 1.2.20. [tick](#tick-1)
* 2. [API函数](#API)
	* 2.1. [npc](#npc-1)
		* 2.1.1. [java.lang.String	executeCommand​(java.lang.String command)](#java.lang.StringexecuteCommandjava.lang.Stringcommand)
		* 2.1.2. [INPCAdvanced	getAdvanced()](#INPCAdvancedgetAdvanced)
		* 2.1.3. [INPCAi	getAi()](#INPCAigetAi)
		* 2.1.4. [INPCDisplay	getDisplay()](#INPCDisplaygetDisplay)
		* 2.1.5. [IDialog	getDialog​(int slot)](#IDialoggetDialogintslot)
		* 2.1.6. [IFaction	getFaction()](#IFactiongetFaction)
		* 2.1.7. [int getHomeX()](#intgetHomeX)
		* 2.1.8. [int getHomeY()](#intgetHomeY)
		* 2.1.9. [int getHomeZ()](#intgetHomeZ)
		* 2.1.10. [INPCInventory	getInventory()](#INPCInventorygetInventory)
		* 2.1.11. [INPCJob getJob()](#INPCJobgetJob)
		* 2.1.12. [INPCRole	getRole()](#INPCRolegetRole)
		* 2.1.13. [INPCStats	getStats()](#INPCStatsgetStats)
		* 2.1.14. [IEntityLivingBase getOwner()](#IEntityLivingBasegetOwner)
		* 2.1.15. [void setHome​(int x, int y, int z)](#voidsetHomeintxintyintz)
		* 2.1.16. [ITimers	getTimers()](#ITimersgetTimers)
		* 2.1.17. [void	giveItem​(IPlayer player, IItemStack item)](#voidgiveItemIPlayerplayerIItemStackitem)
		* 2.1.18. [void	reset()](#voidreset)
		* 2.1.19. [void	say​(java.lang.String message)](#voidsayjava.lang.Stringmessage)
		* 2.1.20. [void	sayTo​(IPlayer player, java.lang.String message)](#voidsayToIPlayerplayerjava.lang.Stringmessage)
		* 2.1.21. [void	setDialog​(int slot, IDialog dialog)](#voidsetDialogintslotIDialogdialog)
		* 2.1.22. [void	setFaction​(int id)](#voidsetFactionintid)
		* 2.1.23. [IProjectile	shootItem​(double x, double y,double z, IItemStack item, int accuracy)](#IProjectileshootItemdoublexdoubleydoublezIItemStackitemintaccuracy)
		* 2.1.24. [IProjectile	shootItem​(IEntityLivingBase target, IItemStack item, int accuracy)](#IProjectileshootItemIEntityLivingBasetargetIItemStackitemintaccuracy)
		* 2.1.25. [void	updateClient()](#voidupdateClient)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

[Custom Npc API官方文档](https://www.kodevelopment.nl/customnpcs/api/1.12.2/) 英文  

# Custom NPC API 详解

##  1. <a name=''></a>钩子函数

使用方法举例：
```python
def attack(c):
    pass # 检测到攻击事件后执行的代码

def damaged(c):
    pass # 检测到受伤事件后执行的代码
```
###  1.1. <a name='npc'></a>npc
共有参数解析:  
`c.npc` 关于npc本身的一些API方法(ICustomNpc)   
`c.API` 一些基础API方法(NpcAPI)   

####  1.1.1. <a name='attack'></a>attack
当npc进行攻击时触发  

特殊参数解析:  
`c.damage` 本次攻击的伤害(float)  
`c.target` 被攻击的对象(IEntityLivingBase)  

####  1.1.2. <a name='damaged'></a>damaged
当npc受伤时触发  

特殊参数解析:  
`c.clearTarget` 暂时未知  
`c.damage`  受到的伤害(float)  
`c.damageSource`  伤害的来源(IDamageSource)  
`c.source` 伤害的来源对象(IEntity)  

####  1.1.3. <a name='died'></a>died
当npc死亡时触发  

特殊参数解析:  
`c.line` 暂时未知(ILine)  
`c.droppedItems`  死亡掉落的物品(IItemStack[])  
`c.damageSource`  死亡的来源(IDamageSource)  
`c.source` 死亡的来源对象(IEntity)  
`c.expDropped` 掉落的经验值(int)  

####  1.1.4. <a name='init'></a>init
当npc初始化时触发  

####  1.1.5. <a name='interact'></a>interact
当与npc交互时触发  

特殊参数解析:  
`c.player` 与npc交互的玩家(IPlayer)  

####  1.1.6. <a name='kill'></a>kill
当npc杀死实体时触发  

特殊参数解析:  

`c.entity` 杀死的实体(IEntityLivingBase)

####  1.1.7. <a name='meleeAttack'></a>meleeAttack
当npc进行近战攻击时触发  

特殊参数解析:  

`c.damage` 本次攻击的伤害(float)  
`c.target` 被攻击的对象(IEntityLivingBase)  

####  1.1.8. <a name='rangedAttack'></a>rangedAttack
当npc进行远程攻击时触发  

特殊参数解析:  

`c.damage` 本次攻击的伤害(float)  
`c.projectiles` 本次攻击的发射物(java.util.List\<IProjectile\>)  
`c.target` 被攻击的对象(IEntityLivingBase)  

####  1.1.9. <a name='target'></a>target
当npc发现敌对实体时触发  

特殊参数解析:   

`c.entity` 敌对的实体(IEntityLivingBase)  

####  1.1.10. <a name='targetLost'></a>targetLost
当npc敌对实体死亡时触发  

特殊参数解析:  

`c.entity` 敌对实体的死亡之前的实体(IEntityLivingBase)  

####  1.1.11. <a name='timer'></a>timer
当关于npc的脚本中定时器触发时触发

特殊参数解析:  
 
`c.id` 定时器的id(int)  

####  1.1.12. <a name='tick'></a>tick
每0.5秒触发一次


###  1.2. <a name='player'></a>player

共有参数解析:  
`c.player` 关于player本身的一些API方法(IPlayer)   
`c.API` 一些基础API方法(NpcAPI)  

####  1.2.1. <a name='attack-1'></a>attack
玩家鼠标左键点击时触发

特殊参数解析:  

`c.target` 玩家左键点击的对象(java.lang.Object)  
`c.type` 对象类型(int)  
0: 空气 1:实体 2:方块


####  1.2.2. <a name='broken'></a>broken
玩家破坏方块时触发

特殊参数解析:  

`c.block` 玩家破坏的方块(IBlock)  
`c.exp` 破坏方块掉落的经验(int)  

####  1.2.3. <a name='chat'></a>chat
玩家在聊天栏说话时触发

特殊参数解析:  

`c.message` 聊天内容(java.lang.String)   

####  1.2.4. <a name='containerClosed'></a>containerClosed
玩家物品栏/容器关闭时触发

特殊参数解析:  

`c.container` 容器对象(IContainer)   

####  1.2.5. <a name='containerOpen'></a>containerOpen
玩家物品栏/容器打开时触发

特殊参数解析:  

`c.container` 容器对象(IContainer)   

####  1.2.6. <a name='damaged-1'></a>damaged
当玩家受伤时触发  

特殊参数解析:  

`c.damage`  受到的伤害(float)  
`c.damageSource`  伤害的来源(IDamageSource)  
`c.source` 伤害的来源对象(IEntity)  

####  1.2.7. <a name='died-1'></a>died
玩家死亡时触发

特殊参数解析:  

`c.damageSource`  造成死亡的来源(IDamageSource)  
`c.source` 造成死亡的来源对象(IEntity)  
`c.type` 造成死亡的类型描述(java.lang.String)

####  1.2.8. <a name='factionUpdate'></a>factionUpdate
玩家阵营点数发生变动时触发

特殊参数解析:  

`c.faction` 阵营(IFaction)  
`c.init` 是否默认对玩家设置了阵营点数(boolean)  
`c.points` 当前阵营点数(int)  


####  1.2.9. <a name='init-1'></a>init
当player初始化时触发  

####  1.2.10. <a name='interact-1'></a>interact
鼠标右键按下触发  

特殊参数解析:  

`c.target` 右键的对象(java.lang.Object)  
`c.type` 右键对象的类型(int)  
0:空气 1:实体 2:方块  

####  1.2.11. <a name='keyPressed'></a>keyPressed
键盘按下触发

特殊参数解析:  

`c.isAltPressed` 是否Alt键按下(boolean)  
`c.isCtrlPressed` 是否Ctrl键按下(boolean)  
`c.isMetaPressed` 是否Windows键按下(boolean)   
`c.isShiftPressed` 是否Shift键按下(boolean)  
`c.key` 按键值(int)  
[按键对照官方英文网址](https://minecraft.fandom.com/wiki/Key_codes)  
[按键对照官方中文网址](https://zh.minecraft.wiki/w/%E9%94%AE%E6%8E%A7%E4%BB%A3%E7%A0%81)  



####  1.2.12. <a name='kill-1'></a>kill
当玩家杀死实体时触发  

特殊参数解析:  

`c.entity` 杀死的实体(IEntityLivingBase)

####  1.2.13. <a name='levelUp'></a>levelUp
当玩家升级时触发

特殊参数解析:

`c.change` 等级改变值(int)  

####  1.2.14. <a name='login'></a>login
玩家登入时触发

####  1.2.15. <a name='logout'></a>logout
玩家退出时触发

####  1.2.16. <a name='pickedUp'></a>pickedUp
玩家拾取一种物品时触发

特殊参数解析:

`c.item` 拾取的物品(IItemStack)

####  1.2.17. <a name='rangedLaunched'></a>rangedLaunched
暂时未知

####  1.2.18. <a name='timer-1'></a>timer
当关于玩家的脚本中定时器触发时触发

特殊参数解析:  
 
`c.id` 定时器的id(int)  

####  1.2.19. <a name='toss'></a>toss
玩家丢弃一种物品时触发

特殊参数解析:

`c.item` 丢弃的物品(IItemStack)

####  1.2.20. <a name='tick-1'></a>tick
每0.5秒触发一次


##  2. <a name='API'></a>API函数

###  2.1. <a name='npc-1'></a>npc
使用方法举例
`c.npc.executeCommand("say Hello")`
`c.npc.say("Hello")`

####  2.1.1. <a name='java.lang.StringexecuteCommandjava.lang.Stringcommand'></a>java.lang.String	executeCommand​(java.lang.String command)  
以npc为执行源执行指令 command
`c.npc.executeCommand("tp @s 100 100 100")`  

####  2.1.2. <a name='INPCAdvancedgetAdvanced'></a>INPCAdvanced	getAdvanced()  
获取高级属性  

####  2.1.3. <a name='INPCAigetAi'></a>INPCAi	getAi()
获取 npc AI  

####  2.1.4. <a name='INPCDisplaygetDisplay'></a>INPCDisplay	getDisplay()
获取 npc 外观属性  

####  2.1.5. <a name='IDialoggetDialogintslot'></a>IDialog	getDialog​(int slot)
获取 npc 在对话槽slot的对话  

####  2.1.6. <a name='IFactiongetFaction'></a>IFaction	getFaction()   
获取 npc 阵营  

####  2.1.7. <a name='intgetHomeX'></a>int getHomeX()  
获取 npc 家位置的 x 坐标  

####  2.1.8. <a name='intgetHomeY'></a>int getHomeY()  
获取 npc 家位置的 y 坐标   

####  2.1.9. <a name='intgetHomeZ'></a>int getHomeZ()  
获取 npc 家位置的 z坐标  

####  2.1.10. <a name='INPCInventorygetInventory'></a>INPCInventory	getInventory()
获取 npc 物品栏

####  2.1.11. <a name='INPCJobgetJob'></a>INPCJob getJob()
获取 npc 职业

####  2.1.12. <a name='INPCRolegetRole'></a>INPCRole	getRole()
获取 npc 角色

####  2.1.13. <a name='INPCStatsgetStats'></a>INPCStats	getStats()
获取 npc 属性

####  2.1.14. <a name='IEntityLivingBasegetOwner'></a>IEntityLivingBase getOwner()
获取 npc 跟随的实体

####  2.1.15. <a name='voidsetHomeintxintyintz'></a>void setHome​(int x, int y, int z)
设置 npc 家

####  2.1.16. <a name='ITimersgetTimers'></a>ITimers	getTimers()
获取 npc 定时器

####  2.1.17. <a name='voidgiveItemIPlayerplayerIItemStackitem'></a>void	giveItem​(IPlayer player, IItemStack item)  
给予玩家物品

####  2.1.18. <a name='voidreset'></a>void	reset() 
重设 npc 

####  2.1.19. <a name='voidsayjava.lang.Stringmessage'></a>void	say​(java.lang.String message)
npc 在聊天栏内说话

####  2.1.20. <a name='voidsayToIPlayerplayerjava.lang.Stringmessage'></a>void	sayTo​(IPlayer player, java.lang.String message)	
npc 在聊天栏对着某玩家说话

####  2.1.21. <a name='voidsetDialogintslotIDialogdialog'></a>void	setDialog​(int slot, IDialog dialog)
将 npc 对话槽内的 slot 号对话 设置为 新对话 dialog

####  2.1.22. <a name='voidsetFactionintid'></a>void	setFaction​(int id)
设置 npc 阵营

####  2.1.23. <a name='IProjectileshootItemdoublexdoubleydoublezIItemStackitemintaccuracy'></a>IProjectile	shootItem​(double x, double y,double z, IItemStack item, int accuracy)
向 x, y, z处以 accuracy 的精准度 发射投掷物 item  
精准度(1~100)

####  2.1.24. <a name='IProjectileshootItemIEntityLivingBasetargetIItemStackitemintaccuracy'></a>IProjectile	shootItem​(IEntityLivingBase target, IItemStack item, int accuracy)
向 目标实体 target 以 accuracy 的精准度 发射投掷物 item  
精准度(1~100)

####  2.1.25. <a name='voidupdateClient'></a>void	updateClient()
强制更新npc(默认半秒更新一次)
