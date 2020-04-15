---
title: ICommandUI 接口
ms.date: 09/07/2019
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
ms.openlocfilehash: 335deefc04a80f47151c5d5e71486e30f9918abd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356631"
---
# <a name="icommandui-interface"></a>ICommandUI 接口

管理用户界面命令。

## <a name="syntax"></a>语法

```
interface class ICommandUI
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[icommandui__Check](#check)|将此命令的用户界面项设置为相应的检查状态。|
|[ICommandUI：：继续路由](#continuerouting)|告诉命令路由机制继续将当前消息路由到处理程序链中。|
|[ICommandUI：已启用](#enabled)|启用或禁用此命令的用户界面项。|
|[ICommandUI：ID](#id)|获取由对象表示的`ICommandUI`用户界面对象的 ID。|
|[ICommandUI：索引](#index)|获取由对象表示的`ICommandUI`用户界面对象的索引。|
|[ICommandUI：：收音机](#radio)|将此命令的用户界面项设置为相应的检查状态。|
|[ICommandUI：文本](#text)|设置此命令的用户界面项的文本。|

## <a name="remarks"></a>备注

此接口提供管理用户界面命令的方法和属性。 `ICommandUI`与[CmCmdUI 类](../../mfc/reference/ccmdui-class.md)类似，只`ICommandUI`不过用于与 .NET 组件互操作的 MFC 应用程序。

`ICommandUI`在[iCommandTarget](../../mfc/reference/icommandtarget-interface.md)派生类中ON_UPDATE_COMMAND_UI处理程序中使用。 当应用程序的用户激活（选择或单击）菜单时，每个菜单项将显示为已启用或禁用。 每个菜单命令的目标通过实现ON_UPDATE_COMMAND_UI处理程序来提供此信息。 对于应用程序中的每个命令用户界面对象，使用[类向导](mfc-class-wizard.md)为每个处理程序创建消息映射条目和函数原型。

有关接口在命令路由中的`ICommandUI`使用方式的详细信息，请参阅[如何：将命令路由添加到 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

有关如何在 MFC 中管理用户界面命令的详细信息，请参阅[CCmdUI 类](../../mfc/reference/ccmdui-class.md)。

## <a name="icommanduicheck"></a><a name="check"></a>ICommandUI：检查

将此命令的用户界面项设置为相应的检查状态。

```
property UICheckState Check;
```

## <a name="remarks"></a>备注

此属性将此命令的用户界面项设置为相应的检查状态。 将"检查"设置为以下值：

- 0 取消选中
- 1 检查
- 2 设置不确定

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a>ICommandUI：：继续路由

告诉命令路由机制继续将当前消息路由到处理程序链中。

```
void ContinueRouting();
```

## <a name="remarks"></a>备注

这是一个高级成员函数，应与返回 FALSE 的ON_COMMAND_EX处理程序结合使用。 有关详细信息，请参阅技术说明 TN006：消息映射。

## <a name="icommanduienabled"></a><a name="enabled"></a>ICommandUI：已启用

启用或禁用此命令的用户界面项。

```
property bool Enabled;
```

## <a name="remarks"></a>备注

此属性启用或禁用此命令的用户界面项。 设置为 TRUE 以启用项目，FALSE 将其禁用。

## <a name="icommanduiid"></a><a name="id"></a>ICommandUI：ID

获取 ICommandUI 对象表示的用户界面对象的 ID。

```
property unsigned int ID;
```

## <a name="remarks"></a>备注

此属性获取菜单项、工具栏按钮或 ICommandUI 对象表示的其他用户界面对象的 ID（句柄）。

## <a name="icommanduiindex"></a><a name="index"></a>ICommandUI：索引

获取由 ICommandUI 对象表示的用户界面对象的索引。

```
property unsigned int Index;
```

## <a name="remarks"></a>备注

此属性获取菜单项、工具栏按钮或 ICommandUI 对象表示的其他用户界面对象的索引（句柄）。

## <a name="icommanduiradio"></a><a name="radio"></a>ICommandUI：：收音机

将此命令的用户界面项设置为相应的检查状态。

```
property bool Radio;
```

## <a name="remarks"></a>备注

此属性将此命令的用户界面项设置为相应的检查状态。 将"无线电"设置为 TRUE 以启用该项目;将"无线电"设置为 TRUE，以启用该项目。否则 FALSE。

## <a name="icommanduitext"></a><a name="text"></a>ICommandUI：文本

设置此命令的用户界面项的文本。

```
property String^ Text;
```

## <a name="remarks"></a>备注

此属性设置此命令的用户界面项的文本。 将文本设置为文本字符串句柄。

## <a name="requirements"></a>要求

**标题**：afxwinforms.h（在程序集 atlmfc_lib_mfcmc80.dll 中定义）

## <a name="see-also"></a>另请参阅

[CmDUI 类](../../mfc/reference/ccmdui-class.md)
