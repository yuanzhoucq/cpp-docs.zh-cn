---
title: CWordArray 类
ms.date: 09/07/2019
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
ms.openlocfilehash: c136bbb14e0d7cffc604813731b6f87ba18063cf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907910"
---
# <a name="cwordarray-class"></a>CWordArray 类

支持 16 位数组。

## <a name="syntax"></a>语法

```
class CWordArray : public CObject
```

## <a name="members"></a>成员

的`CWordArray`成员函数类似于类[CObArray](../../mfc/reference/cobarray-class.md)的成员函数。 由于此相似性，因此你可以使用 `CObArray` 参考文档获取成员函数细节。 无论你在何处看到[CObject](../../mfc/reference/cobject-class.md)指针作为函数参数或返回值，都要用词代替。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，转换为

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|在该数组中返回对元素指针的临时引用。|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|返回给定索引位置处的值。|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|获取此数组中的元素数。|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|获取此数组中的元素数。|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|返回最大的有效索引。|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|确定数组是否为空。|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|从此数组中移除所有元素。|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引处的元素。|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CObArray：： operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

`CWordArray`合并了[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏以支持其元素的序列化和转储。 如果使用重载的插入运算符或[CObject：：串行化](../../mfc/reference/cobject-class.md#serialize)成员函数将一组单词存储到存档，则每个元素依次序列化。

> [!NOTE]
>  在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

如果需要在数组中转储单个元素，则必须将转储上下文的深度设置为1或更大。

有关使用`CWordArray`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

##  <a name="icommandsource_interface"></a>ICommandSource 接口

管理从命令源对象发送到用户控件的命令。

```
interface class ICommandSource
```

### <a name="remarks"></a>备注

在 MFC 视图中承载用户控件时， [CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)将命令和更新命令 UI 消息路由到用户控件，以允许它处理 MFC 命令（例如，框架菜单项和工具栏按钮）。 通过实现，可以为用户控件指定对`ICommandSource`对象的引用。

请参阅[如何：向 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)添加命令路由，以获取有关如何使用`ICommandTarget`的示例。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="addcommandhandler"></a>ICommandSource：： AddCommandHandler

将命令处理程序添加到命令源对象。

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

*cmdHandler*<br/>
命令处理程序方法的句柄。

### <a name="remarks"></a>备注

此方法将命令处理程序*cmdHandler*添加到命令源对象，并将该处理程序映射到*cmdID*。

请参阅[如何：向 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)添加命令路由，以获取有关如何使用`AddCommandHandler`的示例。

##  <a name="addcommandrangehandler"></a>ICommandSource：： AddCommandRangeHandler

向命令源对象添加一组命令处理程序。

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>参数

*cmdIDMin*<br/>
命令 ID 范围的起始索引。

*cmdIDMax*<br/>
命令 ID 范围的结束索引。

*cmdHandler*<br/>
命令映射到的消息处理程序方法的句柄。

### <a name="remarks"></a>备注

此方法将一系列连续的命令 Id 映射到单个消息处理程序，并将其添加到命令源对象。 这用于处理一组具有一种方法的相关按钮。

##  <a name="addcommandrangeuihandler"></a>ICommandSource：： AddCommandRangeUIHandler

向命令源对象添加一组用户界面命令消息处理程序。

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>参数

*cmdIDMin*<br/>
命令 ID 范围的起始索引。

*cmdIDMax*<br/>
命令 ID 范围的结束索引。

*cmdHandler*<br/>
命令映射到的消息处理程序方法的句柄。

### <a name="remarks"></a>备注

此方法将一系列连续的命令 Id 映射到一个用户界面命令消息处理程序，并将其添加到命令源对象。 这用于处理一组具有一种方法的相关按钮。

##  <a name="addcommanduihandler"></a>ICommandSource：： AddCommandUIHandler

向命令源对象添加用户界面命令消息处理程序。

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

*cmdUIHandler*<br/>
用户界面命令消息处理程序方法的句柄。

### <a name="remarks"></a>备注

此方法将用户界面命令消息处理程序*cmdHandler*添加到命令源对象，并将该处理程序映射到*cmdID*。

##  <a name="postcommand"></a>ICommandSource：:P ostCommand

在不等待消息处理的情况下发布消息。

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>参数

*command*<br/>
要发布的消息的命令 ID。

### <a name="remarks"></a>备注

此方法以异步方式发布映射到由*命令*指定的 ID 的消息。 它调用[CWnd：:P ostmessage](../../mfc/reference/cwnd-class.md#postmessage)将消息放入窗口的消息队列中，然后返回而不等待相应的窗口处理该消息。

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

从命令源对象中删除命令处理程序。

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>备注

此方法从命令源对象中删除映射到*cmdID*的命令处理程序。

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

从命令源对象中移除一组命令处理程序。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>参数

*cmdIDMin*<br/>
命令 ID 范围的起始索引。

*cmdIDMax*<br/>
命令 ID 范围的结束索引。

### <a name="remarks"></a>备注

此方法从命令源对象中删除一组消息处理程序，这些消息处理程序映射到由*cmdIDMin*和*cmdIDMax*指定的命令 id。

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

从命令源对象中移除一组用户界面命令消息处理程序。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>参数

*cmdIDMin*<br/>
命令 ID 范围的起始索引。

*cmdIDMax*<br/>
命令 ID 范围的结束索引。

### <a name="remarks"></a>备注

此方法从命令源对象中移除一组用户界面命令消息处理程序，并映射到由*cmdIDMin*和*cmdIDMax*指定的命令 id。

##  <a name="removecommanduihandler"></a>ICommandSource：： RemoveCommandUIHandler

从命令源对象中删除用户界面命令消息处理程序。

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>备注

此方法从命令源对象中删除映射到*cmdID*的用户界面命令消息处理程序。

##  <a name="sendcommand"></a>ICommandSource：： SendCommand

发送消息，并在返回前等待处理。

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>参数

*command*<br/>
要发送的消息的命令 ID。

### <a name="remarks"></a>备注

此方法同步发送映射到由*命令*指定的 ID 的消息。 它调用[CWnd：： SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)将消息放入窗口的消息队列中，并等待该窗口过程在返回前处理该消息。

##  <a name="icommandtarget_interface"></a>ICommandTarget 接口

为用户控件提供一个接口，用于从命令源对象接收命令。

```
interface class ICommandTarget
```

### <a name="remarks"></a>备注

在 MFC 视图中承载用户控件时， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)将命令和更新命令 UI 消息路由到用户控件，以允许它处理 MFC 命令（例如，框架菜单项和工具栏按钮）。 通过实现`ICommandTarget`，可以为用户控件指定对对象的引用。

请参阅[如何：向 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)添加命令路由，以获取有关如何使用`ICommandTarget`的示例。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="initialize"></a>  ICommandTarget::Initialize

初始化命令目标对象。

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>参数

*cmdSource*<br/>
命令源对象的句柄。

### <a name="remarks"></a>备注

在 MFC 视图中承载用户控件时， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)将命令和更新命令 UI 消息路由到用户控件，以允许它处理 MFC 命令。

此方法初始化命令目标对象，并将其与指定的命令源对象*cmdSource*关联。 应在用户控件类实现中调用此方法。 在初始化时，应通过在`Initialize`实现中调用[ICommandSource：： AddCommandHandler](../../mfc/reference/icommandsource-interface.md) ，向命令源对象注册命令处理程序。 请参阅[如何：向 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)添加命令路由，以获取有关如何使用`Initialize`来执行此操作的示例。

##  <a name="icommandui_interface"></a>ICommandUI 接口

管理用户界面命令。

```
interface class ICommandUI
```

### <a name="remarks"></a>备注

此接口提供管理用户界面命令的方法和属性。 `ICommandUI`类似于[CCmdUI 类](../../mfc/reference/ccmdui-class.md)，但用于与`ICommandUI` .net 组件进行互操作的 MFC 应用程序除外。

`ICommandUI`用于派生类中`ON_UPDATE_COMMAND_UI`的处理程序。 当应用程序的用户激活（选择或单击）菜单时，每个菜单项都将显示为 "已启用" 或 "已禁用"。 每个菜单命令的目标通过实现`ON_UPDATE_COMMAND_UI`处理程序来提供此信息。 对于应用程序中的每个命令用户界面对象，使用[类向导](mfc-class-wizard.md)或 "**属性**" 窗口（在**类视图**中）为每个处理程序创建消息映射项和函数原型。

有关如何`ICommandUI`在命令路由中使用接口的详细信息，请参阅[如何：向 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)添加命令路由。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

有关如何在 MFC 中管理用户界面命令的详细信息，请参阅[CCmdUI 类](../../mfc/reference/ccmdui-class.md)。

##  <a name="check"></a>ICommandUI：： Check

将此命令的用户界面项设置为相应的复选状态。

```
property UICheckState Check;
```

### <a name="remarks"></a>备注

此属性将此命令的用户界面项设置为相应的复选状态。 设置`Check`为以下值：

|术语|定义|
|----------|----------------|
|0|选定|
|1|检查|
|2|设置不确定|

##  <a name="continuerouting"></a>ICommandUI::ContinueRouting

告诉命令路由机制继续向下传递处理程序链中的当前消息。

```
void ContinueRouting();
```

### <a name="remarks"></a>备注

这是一个高级成员函数，应与返回 FALSE 的[ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex)处理程序结合使用。 有关详细信息，请参阅技术[说明 TN006：消息映射](../../mfc/tn006-message-maps.md)。

##  <a name="enabled"></a>ICommandUI：： Enabled

启用或禁用此命令的用户界面项。

```
property bool Enabled;
```

### <a name="remarks"></a>备注

此属性将启用或禁用此命令的用户界面项。 设置`Enabled`为 TRUE 可启用项，设置为 FALSE 可禁用项。

##  <a name="id"></a>ICommandUI：： ID

获取由`ICommandUI`对象表示的用户界面对象的 ID。

```
property unsigned int ID;
```

### <a name="remarks"></a>备注

此属性获取由`ICommandUI`对象表示的菜单项、工具栏按钮或其他用户界面对象的 ID （一个句柄）。

##  <a name="index"></a>ICommandUI：： Index

获取由`ICommandUI`对象表示的用户界面对象的索引。

```
property unsigned int Index;
```

### <a name="remarks"></a>备注

此属性获取由`ICommandUI`对象表示的菜单项、工具栏按钮或其他用户界面对象的索引（句柄）。

##  <a name="radio"></a>ICommandUI：：收音机

将此命令的用户界面项设置为相应的复选状态。

```
property bool Radio;
```

### <a name="remarks"></a>备注

此属性将此命令的用户界面项设置为相应的复选状态。 设置`Radio`为 TRUE 以启用项; 否则设置为 FALSE。

##  <a name="text"></a>ICommandUI：： Text

为此命令设置用户界面项的文本。

```
property String^ Text;
```

### <a name="remarks"></a>备注

此属性设置此命令的用户界面项的文本。 设置`Text`为文本字符串句柄。

##  <a name="iview_interface"></a>IView 接口

实现多种方法， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)使用这些方法将视图通知发送到托管控件。

```
interface class IView
```

### <a name="remarks"></a>备注

`IView`实现多种方法， `CWinFormsView`这些方法使用将常见视图通知转发到托管托管控件。 这些是[OnInitialUpdate](../../mfc/reference/iview-interface.md)、 [OnUpdate](../../mfc/reference/iview-interface.md)和[OnActivateView](../../mfc/reference/iview-interface.md)。

`IView`类似于[CView](../../mfc/reference/cview-class.md)，但仅用于托管视图和控件。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="onactivateview"></a>IView：： OnActivateView

当激活或停用视图时，由 MFC 调用。

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>参数

*activate*<br/>
指示是否正在激活或停用视图。

##  <a name="oninitialupdate"></a>IView：： OnInitialUpdate

在视图第一次附加到文档之后但最初显示视图之前由框架调用。

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>IView：： OnUpdate

在视图的文档被修改后由 MFC 调用。

```
void OnUpdate();
```

### <a name="remarks"></a>备注

此函数允许视图更新其显示以反映修改。

## <a name="see-also"></a>请参阅

[MFC 示例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
