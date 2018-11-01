---
title: ICommandUI 接口
ms.date: 11/04/2016
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
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: dd5f79b8ecd65428ce1231777fa6632777859a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467088"
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
|[ICommandUI::ContinueRouting](#continuerouting)|告知继续路由处理程序链中向下的当前消息的命令传送机制。|
|[ICommandUI::Enabled](#enabled)|启用或禁用此命令的用户界面项目。|
|[ICommandUI::ID](#id)|获取所表示的用户界面对象的 ID`ICommandUI`对象。|
|[ICommandUI::Index](#index)|获取所表示的用户界面对象的索引`ICommandUI`对象。|
|[ICommandUI::Radio](#radio)|将此命令的用户界面项设置为相应的复选状态。|
|[ICommandUI::Text](#text)|设置此命令的用户界面项的文本。|

## <a name="remarks"></a>备注

此接口提供方法和属性的管理用户界面命令。 `ICommandUI` 类似于[CCmdUI 类](../../mfc/reference/ccmdui-class.md)，只不过`ICommandUI`用于与.NET 组件进行互操作的 MFC 应用程序。

`ICommandUI` 中的 ON_UPDATE_COMMAND_UI 处理程序中使用，而[ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-派生的类。 时应用程序的用户激活 （选择或单击） 菜单中，每个菜单项显示为已启用或禁用。 每个菜单命令的目标来实现的 ON_UPDATE_COMMAND_UI 处理提供此信息。 对于每个命令用户界面对象在应用程序中，使用属性窗口创建消息映射条目和每个处理程序的函数原型。

有关详细信息如何`ICommandUI`路由命令中使用接口，请参阅[如何： 向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

有关如何在 MFC 中管理用户界面命令的详细信息，请参阅[CCmdUI 类](../../mfc/reference/ccmdui-class.md)。

## <a name="check"></a> ICommandUI::Check

将此命令的用户界面项设置为相应的复选状态。
```
property UICheckState Check;
```

## <a name="remarks"></a>备注

此属性将此命令的用户界面项设置为相应的复选状态。 将检查设置为以下值：
- 取消选中将 0
- 1 检查
- 设置不确定的 2

## <a name="continuerouting"></a> ICommandUI::ContinueRouting

指示命令路由机制，以继续路由处理程序链中向下的当前消息。
```
void ContinueRouting();
```

## <a name="remarks"></a>备注

这是应返回 FALSE 的 ON_COMMAND_EX 处理程序结合使用的高级的成员函数。 有关详细信息，请参阅技术注意 TN006： 消息映射。

## <a name="enabled"></a> ICommandUI::Enabled

启用或禁用此命令的用户界面项目。
```
property bool Enabled;
```

## <a name="remarks"></a>备注

此属性启用或禁用此命令的用户界面项目。 将已启用到设置为 true 以启用该项目，为 FALSE，则将其禁用。

## <a name="id"></a> ICommandUI::ID

获取由 ICommandUI 对象表示的用户界面对象的 ID。
```
property unsigned int ID;
```

## <a name="remarks"></a>备注

此属性获取的菜单项、 工具栏按钮或 ICommandUI 对象表示的其他用户界面对象的 ID （句柄）。

## <a name="index"></a> ICommandUI::Index

获取由 ICommandUI 对象表示的用户界面对象的索引。
```
property unsigned int Index;
```

## <a name="remarks"></a>备注

此属性获取的菜单项、 工具栏按钮或 ICommandUI 对象表示的其他用户界面对象的索引 （句柄）。

## <a name="radio"></a> ICommandUI::Radio

将此命令的用户界面项设置为相应的复选状态。
```
property bool Radio;
```

## <a name="remarks"></a>备注

此属性将此命令的用户界面项设置为相应的复选状态。 将广播到设置为 true 以启用项;否则为 FALSE。

## <a name="text"></a> ICommandUI::Text

设置此命令的用户界面项的文本。
```
property String^ Text;
```

## <a name="remarks"></a>备注

此属性设置为此命令的用户界面项的文本。 将文本设置为文本字符串句柄。

## <a name="requirements"></a>要求

**标头：** afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）

## <a name="see-also"></a>请参阅

[CCmdUI 类](../../mfc/reference/ccmdui-class.md)
