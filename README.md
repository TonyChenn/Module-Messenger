# Module-Messenger
Unity插件-消息机制，用于代码解耦合。

# 使用方法

> 例子：在按下拍照按钮后通知刷新好友面板
- 步骤1、创建一个联合类<kbd>MessangerEventDef</kbd>(插件包安装后就无法修改了)
- 步骤2、添加事件字段，该字段具有唯一性在<kbd>MessangerEventDef</kbd>脚本（可以每个功能都有一个事件字段脚本，类似于消息）中添加字```Demo_EventType```.
- 步骤3、广播事件：在按下拍照按钮方法中调用
```csharp
Messenger.Broadcast(MessangerEventDef.Demo_EventType);
```
- 步骤4、在OnEnable()方法中注册事件：在要监听的脚本中的OnEnable方法中添加监听：
```csharp
Messenger.AddListener(MessangerEventDef.Demo_EventType, OnCall);
```
- 步骤5、在OnDisable()方法中移除事件：在要监听的脚本中的OnDisable方法中移除监听：
```csharp
Messenger.RemoveListener(MessangerEventDef.Demo_EventType, OnCall);
void OnCall()
{
	Debug.Log("===OnCall==");
	//TODO 刷新好友相关代码
}
```
# 注意事项
AddListener和RemoveListener必须成对出现。