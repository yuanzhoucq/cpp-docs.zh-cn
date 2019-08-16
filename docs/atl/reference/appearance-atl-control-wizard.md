---
title: 外观，ATL 控件向导
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: e07dc017241848f1a670c17b12c2254de6d1b8e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492189"
---
# <a name="appearance-atl-control-wizard"></a>外观，ATL 控件向导

使用向导的此页可以标识控件的其他用户元素选项。 此页可用于在 "[选项"、"ATL 控件向导](../../atl/reference/options-atl-control-wizard.md)" 页上的 "**控件类型**" 下标识为**标准控件**的控件。

## <a name="uielement-list"></a>UIElement 列表

- **查看状态**

   设置容器中控件的外观。

   - 不**透明**:设置[VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus)枚举中的 VIEWSTATUS_OPAQUE 位, 并绘制传递到[CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法的整个控件矩形。 控件完全不透明, 且不会显示在控件边界之后。

      此设置有助于容器更快速地绘制控件。 如果未选择此选项, 则控件可以包含透明部分。

      只有不透明控件才能具有纯色背景。

   - **纯色背景**:设置 VIEWSTATUS 枚举中的 VIEWSTATUS_SOLIDBKGND 位。 控件的背景将显示为无图案的纯色。

      此选项仅在同时选择了 "不**透明**" 选项时才可用。

- **添加控件基于**

   通过将[CContainedWindow](ccontainedwindowt-class.md)数据成员添加到实现控件的类, 将控件设置为基于 Windows 控件类型。 它还添加消息映射和消息处理程序函数来处理控件的 Windows 消息。 从列表中选择要创建的 Windows 控件的类型 (如果有)。

   - **Button**

   - **ListBox**

   - **SysAnimate32**

   - **SysListView32**

   - **组合框**

   - **RichEdit**

   - **SysDateTimePick32**

   - **SysMonthCal32**

   - **ComboBoxEx32**

   - **滚动条**

   - **SysHeader32**

   - **SysTabControl32**

   - **编辑**

   - **Static**

   - **SysIPAddress32**

   - **SysTreeView32**

- **杂项状态**

   为控件设置其他外观和行为选项。

   - **在运行时不可见**:将控件设置为在运行时不可见。 你可以使用不可见的控件在后台执行操作, 如按固定的时间间隔触发事件。

   - **作用类似按钮**:设置[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)枚举中的 OLEMISC_ACTSLIKEBUTTON 位, 使控件可像按钮一样操作。 如果容器已将控件的客户端站点标记为默认按钮, 则选择此选项可使按钮控件通过使用较宽的帧绘制自身来将其显示为默认按钮。 有关详细信息, 请参阅[CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) 。

   - **作用类似标签**:设置 OLEMISC 枚举中的 OLEMISC_ACTSLIKELABEL 位, 以使控件能够替换容器的本机标签。 容器确定如何处理此标志 (如果有)。

- **其他**

   为控件设置其他行为选项。

   - **规范化 DC**:设置控件以在调用以绘制自身时创建规范化的设备上下文。 此操作可标准化控件的外观, 但使绘图效率更低。

   - **仅限窗口**:指定控件不能是无窗口的。 如果未选择此选项, 则控件将在支持无窗口对象的容器中自动无窗口, 并且会自动在不支持无窗口对象的容器中进行窗口化。 如果选择此选项, 则即使在支持无窗口对象的容器中, 也会强制控制控件。

   - **插入**:选择此选项可使控件显示在应用程序 (如 Word 和 Excel) 的 "**插入对象**" 对话框中。 然后, 通过此对话框支持嵌入对象的任何应用程序都可以插入控件。

## <a name="see-also"></a>请参阅

[ATL 控件向导](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT 示例:超类 a 标准 Windows 控件](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
