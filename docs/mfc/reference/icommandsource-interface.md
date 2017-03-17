---
title: "ICommandSource 界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ICommandSource interface
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f923a8a42327cb74ce9323f72aae90c7411da27c
ms.lasthandoff: 02/24/2017

---
# <a name="icommandsource-interface"></a>ICommandSource 接口
管理命令从命令源对象发送到用户控件。  
  
## <a name="syntax"></a>语法  
  
```  
interface class ICommandSource  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[ICommandSource::AddCommandHandler](#addcommandhandler)|将命令处理程序添加到命令源对象。|  
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|将一组命令处理程序添加到命令源对象。|  
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|将一组用户界面的命令消息处理程序添加到命令源对象。|  
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|将用户界面命令消息处理程序添加到命令源对象。|  
|[ICommandSource::PostCommand](#postcommand)|将消息发送而无需等待被处理。|  
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|从命令源对象中删除命令处理程序。|  
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|从命令源对象中删除一组命令处理程序。|  
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|从命令源对象中删除一组用户界面的命令消息处理程序。|  
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|从命令源对象中删除一个用户界面命令消息处理程序。|  
|[ICommandSource::SendCommand](#sendcommand)|发送一条消息并等待在返回之前要处理。|  
  
### <a name="remarks"></a>备注  
 当宿主中 MFC 视图的用户控件时[CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)路由命令和更新命令 UI 向用户控件的消息以允许它处理 MFC 命令 （例如，框架菜单项和工具栏按钮）。 通过实现[ICommandTarget 接口](../../mfc/reference/icommandtarget-interface.md)，让用户能够控制对引用`ICommandSource`对象。  
  
 请参阅[如何︰ 向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)以举例说明如何使用`ICommandTarget`。  
  
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxwinforms.h (在程序集 atlmfc\lib\mfcmifc80.dll 中定义)  
  
## <a name="addcommandhandler"></a>ICommandSource::AddCommandHandler
将命令处理程序添加到命令源对象。
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>参数  
`cmdID`  
命令 ID。  
`cmdHandler`  
命令处理程序方法的句柄。

### <a name="remarks"></a>备注
此方法将命令处理程序 cmdHandler 添加到命令源对象，并将该处理程序映射到 cmdID。
请参阅[如何︰ 向 Windows 窗体控件添加命令传送](https://msdn.microsoft.com/library/y33d8624.aspx)以举例说明如何使用 AddCommandHandler。

## <a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

将一组命令处理程序添加到命令源对象。
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```
### <a name="parameters"></a>参数  
`cmdIDMin`  
命令 ID 范围的起始索引。
`cmdIDMax`  
命令 ID 范围的结束索引。
`cmdHandler`  
命令映射到的消息处理程序方法的句柄。
### <a name="remarks"></a>备注
此方法将一组连续的命令 Id 映射到单个消息处理程序，并将其添加到命令源对象。 这适用于带有一种方法处理一组相关的按钮。

## <a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler
将一组用户界面的命令消息处理程序添加到命令源对象。
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin, 
    unsigned int cmdIDMax, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>参数  
`cmdIDMin`  
命令 ID 范围的起始索引。
`cmdIDMax`  
命令 ID 范围的结束索引。
`cmdHandler`  
命令映射到的消息处理程序方法的句柄。

### <a name="remarks"></a>备注
此方法将一组连续的命令 Id 映射到单个用户界面命令消息处理程序，并将其添加到命令源对象。 这适用于带有一种方法处理一组相关的按钮。

## <a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler
将用户界面命令消息处理程序添加到命令源对象。
```
void AddCommandUIHandler(
    unsigned int cmdID, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>参数
`cmdID`  
命令 ID。  
`cmdUIHandler`  
用户界面命令消息处理程序方法的句柄。

### <a name="remarks"></a>备注
此方法将用户界面命令消息处理程序 cmdHandler 添加到命令源对象，并将该处理程序映射到 cmdID。

## <a name="postcommand"></a>ICommandSource::PostCommand
将消息发送而无需等待被处理。
```
void PostCommand(unsigned int command);
```
### <a name="parameters"></a>参数
`command`  
要发布的消息的命令 ID。
### <a name="remarks"></a>备注
此方法以异步方式发送消息映射到指定的命令的 ID。 它调用 CWnd::PostMessage 将消息放入窗口的消息队列，然后返回而不等待相应的窗口来处理该消息。


## <a name="removecommandhandler"></a>ICommandSource::RemoveCommandHandler
从命令源对象中删除命令处理程序。
```
void RemoveCommandHandler(unsigned int cmdID);
```
### <a name="parameters"></a>参数
`cmdID`  
命令 ID。
### <a name="remarks"></a>备注
此方法移除映射到 cmdID 命令源对象中的命令处理程序。


## <a name="removecommandrangecommandhandler"></a>ICommandSource::RemoveCommandRangeHandler 
从命令源对象中删除一组命令处理程序。
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>参数
`cmdIDMin`  
命令 ID 范围的起始索引。
`cmdIDMax`  
命令 ID 范围的结束索引。
### <a name="remarks"></a>备注
此方法移除消息处理程序，从命令源对象由 cmdIDMin 和 cmdIDMax，映射到指定的命令 Id 的组。

## <a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler 
从命令源对象中删除一组用户界面的命令消息处理程序。
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>参数
`cmdIDMin`  
命令 ID 范围的起始索引。
`cmdIDMax`  
命令 ID 范围的结束索引。
### <a name="remarks"></a>备注
此方法中删除一组用户界面命令消息处理程序，命令源对象中由 cmdIDMin 和 cmdIDMax，映射到指定的命令 Id。

## <a name="removecommanduihandler"></a>ICommandSource::RemoveCommandUIHandler 
从命令源对象中删除一个用户界面命令消息处理程序。
```
void RemoveCommandUIHandler(unsigned int cmdID);
```
### <a name="parameters"></a>参数
`cmdID`  
命令 ID。
### <a name="remarks"></a>备注
此方法中删除的用户界面命令消息处理程序映射到 cmdID 命令源对象中。

## <a name="sendcommand"></a>ICommandSource::SendCommand 
发送一条消息并等待在返回之前要处理。
```
void SendCommand(unsigned int command);
```
### <a name="parameters"></a>参数
`command`  
要发送的消息的命令 ID。
### <a name="remarks"></a>备注
此方法以同步方式发送消息映射到指定的命令的 ID。 它调用 CWnd::SendMessage 将消息放在窗口的消息队列中，并一直等待，直到该窗口过程在返回之前处理完的消息。
## <a name="see-also"></a>另请参阅  
 [如何︰ 将命令添加路由到 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandTarget 接口](../../mfc/reference/icommandtarget-interface.md)

