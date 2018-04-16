---
title: "ICommandUI 接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
dev_langs:
- C++
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4971ceaea57b91ff708315a2c32c7bac2801798f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="icommandui-interface"></a>ICommandUI 接口
管理用户界面命令。  
  
## <a name="syntax"></a>语法  
  
```  
interface class ICommandUI  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[icommandui__Check](#check)|将此命令的用户界面项设置为相应的复选状态。|  
|[ICommandUI::ContinueRouting](#continuerouting)|告知继续路由当前消息的处理程序项链的命令传送机制。|  
|[ICommandUI::Enabled](#enabled)|启用或禁用此命令的用户界面项。|  
|[ICommandUI::ID](#id)|获取所表示的用户界面对象的 ID`ICommandUI`对象。|  
|[ICommandUI::Index](#index)|获取所表示的用户界面对象的索引`ICommandUI`对象。|  
|[ICommandUI::Radio](#radio)|将此命令的用户界面项设置为相应的复选状态。|  
|[ICommandUI::Text](#text)|设置此命令的用户界面项的文本。|  
  
## <a name="remarks"></a>备注  
 此接口提供方法和属性，管理用户界面命令。 `ICommandUI`类似于[CCmdUI 类](../../mfc/reference/ccmdui-class.md)，只不过`ICommandUI`用于 MFC 应用程序与.NET 组件进行互操作。  
  
 `ICommandUI`在中使用`ON_UPDATE_COMMAND_UI`中的处理程序[ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-派生类。 当应用程序的用户激活 （选择或单击） 菜单上，每个菜单项将显示为已启用或禁用。 每个菜单命令的目标提供此信息通过实现`ON_UPDATE_COMMAND_UI`处理程序。 对于每个命令用户界面对象，应用程序中，使用属性窗口创建消息映射项和每个处理程序的函数原型。  
  
 有关详细信息如何`ICommandUI`接口用于命令路由，请参阅[如何： 向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。  
  
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
 在 MFC 中如何管理用户界面命令的详细信息，请参阅[CCmdUI 类](../../mfc/reference/ccmdui-class.md)。  
  
## <a name="check"></a>ICommandUI::Check  
将此命令的用户界面项设置为相应的复选状态。
```
property UICheckState Check;
```
## <a name="remarks"></a>备注  
此属性将此命令的用户界面项设置为相应的复选状态。 将检查设置为以下值：  
- 0 请先取消选中  
- 1 检查  
- 不确定设置 2  

## <a name="continuerouting"></a>ICommandUI::ContinueRouting   
告知继续路由当前消息的处理程序项链的命令路由机制。
```
void ContinueRouting();
```
## <a name="remarks"></a>备注
这是一个高级的成员函数，应使用结合的 ON_COMMAND_EX 处理程序，则返回 FALSE。 有关详细信息，请参阅技术注意 TN006： 消息映射。

## <a name="enabled"></a>ICommandUI::Enabled 
启用或禁用此命令的用户界面项。
```
property bool Enabled;
```
## <a name="remarks"></a>备注
此属性启用或禁用此命令的用户界面项。 为 true 以启用该项目，为 false，则禁用该设置到已启用。

## <a name="id"></a>ICommandUI::ID  
获取由 ICommandUI 对象表示的用户界面对象的 ID。
```
property unsigned int ID;
```
## <a name="remarks"></a>备注
此属性获取菜单项、 工具栏按钮或由 ICommandUI 对象代表其他用户界面对象的 ID （句柄）。

## <a name="index"></a>ICommandUI::Index   
获取由 ICommandUI 对象表示的用户界面对象的索引。
```
property unsigned int Index;
```
## <a name="remarks"></a>备注
此属性获取的菜单项、 工具栏按钮或由 ICommandUI 对象代表其他用户界面对象的索引 （句柄）。

## <a name="radio"></a>ICommandUI::Radio 
将此命令的用户界面项设置为相应的复选状态。
```
property bool Radio;
```
## <a name="remarks"></a>备注
此属性将此命令的用户界面项设置为相应的复选状态。 为 true 以启用项; 设置为单选否则为 FALSE。

## <a name="text"></a>ICommandUI::Text 
设置此命令的用户界面项的文本。
```
property String^ Text;
```
## <a name="remarks"></a>备注
此属性设置为此命令的用户界面项的文本。 将文本设置为文本字符串句柄。

## <a name="requirements"></a>惠?  
 **标头：** afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）  
  
## <a name="see-also"></a>请参阅  
 [CCmdUI 类](../../mfc/reference/ccmdui-class.md)
