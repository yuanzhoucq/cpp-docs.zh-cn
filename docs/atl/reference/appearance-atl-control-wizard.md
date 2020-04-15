---
title: 外观，ATL 控件向导
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 3484fb5d0f919af0dfd18b584e96d4675e2baea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319395"
---
# <a name="appearance-atl-control-wizard"></a>外观，ATL 控件向导

使用向导的此页面标识控件的其他用户元素选项。 此页面可用于在["选项、ATL 控制向导](../../atl/reference/options-atl-control-wizard.md)"页上标识为 **"控制"类型**下**的标准控件**的控件。

## <a name="uielement-list"></a>UIElement 列表

- **查看状态**

   设置容器内控件的外观。

  - **不透明**：设置[视图状态](/windows/win32/api/ocidl/ne-ocidl-viewstatus)枚举中的VIEWSTATUS_OPAQUE位，并绘制传递给[CComControlBase：：onDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法的整个控件矩形。 控件显示为完全不透明，并且没有任何容器显示在控制边界后面。

      此设置可帮助容器更快地绘制控件。 如果未选择此选项，则控件可以包含透明部件。

      只有不透明控件才能具有实体背景。

  - **实体背景**：设置视图状态枚举中的VIEWSTATUS_SOLIDBKGND位。 控件的背景显示为纯色，没有图案。

      仅当也选择了 **"不透明"** 选项时，此选项才可用。

- **基于**

   通过将[CContainedWindow](ccontainedwindowt-class.md)数据成员添加到实现控件的类，将控件设置为基于 Windows 控件类型。 它还添加消息映射和消息处理程序函数来处理控件的 Windows 消息。 从列表中选择要创建的 Windows 控件的类型（如果有）。

  - **按钮**

  - **ListBox**

  - **SysAnimate32**

  - **SysListView32**

  - **组合框**

  - **丰富编辑**

  - **SysDateTimePick32**

  - **SysMonthCal32**

  - **ComboBoxEx32**

  - **ScrollBar**

  - **SysHeader32**

  - **SysTabControl32**

  - **编辑**

  - **静态**

  - **SysIPAddress32**

  - **SysTreeView32**

- **杂项状态**

   为控件设置其他外观和行为选项。

  - **运行时不可见**：将控件设置为运行时不可见。 可以使用不可见控件在后台执行操作，例如以时序间隔触发事件。

  - **操作类似于按钮**：在[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)枚举中设置OLEMISC_ACTSLIKEBUTTON位，使控件能够像按钮一样操作。 如果容器将控件的客户端站点标记为默认按钮，则选择此选项可使按钮控件通过使用较粗的框架绘制自身来将自己显示为默认按钮。 有关详细信息[，请参阅 CComControlBase：获取环境显示作为默认](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)信息。

  - **像标签一样：** 在 OLEMISC 枚举中设置OLEMISC_ACTSLIKELABEL位，使控件能够替换容器的本机标签。 容器确定如何处理此标志（如果有）。

- **其他**

   为控件设置其他行为选项。

  - **规范化 DC**： 设置控件，在调用它绘制自身时创建规范化的设备上下文。 此操作使控件的外观标准化，但会使绘图效率降低。

  - **仅窗口**：指定控件不能无窗口。 如果不选择此选项，控件在支持无窗口对象的容器中自动无窗口，并且它会自动在不支持无窗口对象的容器中窗口。 选择此选项将强制控件窗口化，即使在支持无窗口对象的容器中也是如此。

  - **可插入**：选择此选项可使控件显示在"**插入对象"** 对话框中的应用程序（如 Word 和 Excel）中。 然后，任何支持嵌入对象的应用程序都可以通过此对话框插入您的控件。

## <a name="see-also"></a>另请参阅

[ATL 控件向导](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT 示例：超类标准 Windows 控件](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
