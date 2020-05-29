---
title: ICommandSource 接口
ms.date: 03/27/2019
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: 6a03c46c972f7746f39a3c5c65ca9b5509983d59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356979"
---
# <a name="icommandsource-interface"></a>ICommandSource 接口

管理从命令源对象发送到用户控件的命令。

## <a name="syntax"></a>语法

```cpp
interface class ICommandSource
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[ICommand 来源：添加命令处理程序](#addcommandhandler)|将命令处理程序添加到命令源对象。|
|[ICommand 来源：添加命令源处理程序](#addcommandrangehandler)|将一组命令处理程序添加到命令源对象。|
|[ICommand 来源：添加命令RangeUIHandler](#addcommandrangeuihandler)|将一组用户界面命令消息处理程序添加到命令源对象。|
|[ICommand 来源：添加命令UIHandler](#addcommandrangeuihandler)|将用户界面命令消息处理程序添加到命令源对象。|
|[ICommand 来源：:PostCommand](#postcommand)|发布消息，无需等待处理。|
|[ICommand 来源：删除命令处理程序](#removecommandhandler)|从命令源对象中删除命令处理程序。|
|[ICommand 来源：删除命令源处理程序](#removecommandrangehandler)|从命令源对象中删除一组命令处理程序。|
|[ICommand 来源：删除命令RangeUIHandler](#removecommandrangeuihandler)|从命令源对象中删除一组用户界面命令消息处理程序。|
|[ICommand 来源：删除命令UIHandler](#removecommandrangeuihandler)|从命令源对象中删除用户界面命令消息处理程序。|
|[ICommand 来源：发送命令](#sendcommand)|发送消息并等待处理它，然后再返回。|

### <a name="remarks"></a>备注

当您在 MFC 视图中托管用户控件时[，CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)会将命令和命令 UI 消息更新到用户控件，以允许它处理 MFC 命令（例如，框架菜单项和工具栏按钮）。 通过实现[ICommandTarget 接口](../../mfc/reference/icommandtarget-interface.md)，您可以为用户提供对`ICommandSource`对象的引用。

有关如何使用，请参阅[：将命令路由添加到 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)`ICommandTarget`。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>要求

**标题**：afxwinforms.h（在程序集 atlmfc_lib_mfcmc80.dll 中定义）

## <a name="icommandsourceaddcommandhandler"></a><a name="addcommandhandler"></a>ICommand 来源：添加命令处理程序

将命令处理程序添加到命令源对象。

```cpp
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

此方法将命令处理程序 cmdHandler 添加到命令源对象，并将处理程序映射到 cmdID。
有关如何使用 AddCommandHandler 的示例，请参阅[：将命令路由添加到 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

## <a name="icommandsourceaddcommandrangehandler"></a><a name="addcommandrangehandler"></a>ICommand 来源：添加命令源处理程序

将一组命令处理程序添加到命令源对象。

```cpp
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>参数

*厘米德明*<br/>
命令 ID 范围的开头索引。
*cmdIDMax*<br/>
命令 ID 范围的结束索引。
*cmdHandler*<br/>
命令映射到的消息处理程序方法的句柄。

### <a name="remarks"></a>备注

此方法将连续范围的命令指示映射到单个消息处理程序，并将其添加到命令源对象。 这用于使用一种方法处理一组相关按钮。

## <a name="icommandsourceaddcommandrangeuihandler"></a><a name="addcommandrangeuihandler"></a>ICommand 来源：添加命令RangeUIHandler

将一组用户界面命令消息处理程序添加到命令源对象。

```cpp
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>参数

*厘米德明*<br/>
命令 ID 范围的开头索引。
*cmdIDMax*<br/>
命令 ID 范围的结束索引。
*cmdHandler*<br/>
命令映射到的消息处理程序方法的句柄。

### <a name="remarks"></a>备注

此方法将连续范围的命令指示映射到单个用户界面命令消息处理程序，并将其添加到命令源对象。 这用于使用一种方法处理一组相关按钮。

## <a name="icommandsourceaddcommanduihandler"></a><a name="addcommanduihandler"></a>ICommand 来源：添加命令UIHandler

将用户界面命令消息处理程序添加到命令源对象。

```cpp
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

此方法将用户界面命令消息处理程序 cmdHandler 添加到命令源对象，并将处理程序映射到 cmdID。

## <a name="icommandsourcepostcommand"></a><a name="postcommand"></a>ICommand 来源：:PostCommand

发布消息，无需等待处理。

```cpp
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>参数

*命令*<br/>
要过帐的消息的命令 ID。

### <a name="remarks"></a>备注

此方法异步发布映射到命令指定的 ID 的消息。 它调用 CWnd：:PostMessage 将消息放在窗口的消息队列中，然后返回而不等待相应的窗口来处理消息。

## <a name="icommandsourceremovecommandhandler"></a><a name="removecommandhandler"></a>ICommand 来源：删除命令处理程序

从命令源对象中删除命令处理程序。

```cpp
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>备注

此方法从命令源对象中删除映射到 cmdID 的命令处理程序。

## <a name="icommandsourceremovecommandrangehandler"></a><a name="removecommandrangehandler"></a>ICommand 来源：删除命令源处理程序

从命令源对象中删除一组命令处理程序。

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>参数

*厘米德明*<br/>
命令 ID 范围的开头索引。
*cmdIDMax*<br/>
命令 ID 范围的结束索引。

### <a name="remarks"></a>备注

此方法从命令源对象中删除一组消息处理程序，这些处理程序映射到 cmdIDMin 和 cmdIDMax 指定的命令 ID。

## <a name="icommandsourceremovecommandrangeuihandler"></a><a name="removecommandrangeuihandler"></a>ICommand 来源：删除命令RangeUIHandler

从命令源对象中删除一组用户界面命令消息处理程序。

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>参数

*厘米德明*<br/>
命令 ID 范围的开头索引。
*cmdIDMax*<br/>
命令 ID 范围的结束索引。

### <a name="remarks"></a>备注

此方法从命令源对象中删除一组用户界面命令消息处理程序，这些处理程序映射到 cmdIDMin 和 cmdIDMax 指定的命令 ID。

## <a name="icommandsourceremovecommanduihandler"></a><a name="removecommanduihandler"></a>ICommand 来源：删除命令UIHandler

从命令源对象中删除用户界面命令消息处理程序。

```cpp
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>备注

此方法从命令源对象中删除映射到 cmdID 的用户界面命令消息处理程序。

## <a name="icommandsourcesendcommand"></a><a name="sendcommand"></a>ICommand 来源：发送命令

发送消息并等待处理它，然后再返回。

```cpp
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>参数

*命令*<br/>
要发送的消息的命令 ID。

### <a name="remarks"></a>备注

此方法同步发送映射到命令指定的 ID 的消息。 它调用 CWnd：：SendMessage 将消息放在窗口的消息队列中，并等待该窗口过程处理该消息后再返回。

## <a name="see-also"></a>另请参阅

[如何：向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget 接口](../../mfc/reference/icommandtarget-interface.md)
