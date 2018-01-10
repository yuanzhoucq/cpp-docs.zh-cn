---
title: "外观，ATL 控件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.control.misc
dev_langs: C++
helpviewer_keywords: ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8869df577dfbc541b989beb4b4f3117d7d12feea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="appearance-atl-control-wizard"></a>外观，ATL 控件向导
在此处插入摘要的"搜索结果"。  
  
 向导的此页用于标识控件的其他用户元素选项。 此页将可用的控件标识为**标准控件**下**控件类型**上[选项，ATL 控件向导](../../atl/reference/options-atl-control-wizard.md)页。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **查看状态**  
 设置容器内控件的外观。  
  
-   **不透明**： 集`VIEWSTATUS_OPAQUE`中位[VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)枚举和绘制整个控件矩形传递给[CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法。 该控件会出现完全不透明，和容器的任何部分显示背后的控件边界不显示。  
  
     此设置可帮助更快地绘制控件的容器。 如果不选择此选项，该控件可以包含透明的部分。  
  
     仅不透明的控件可以具有纯色背景。  
  
-   集`VIEWSTATUS_SOLIDBKGND`中位`VIEWSTATUS`枚举。 控件的背景显示为具有无模式的纯色。  
  
     此选项才可用才**不透明**还选择选项。  
  
 **添加基于控制**  
 设置要通过添加基于 Windows 控件类型的控件[CContainedWindow](ccontainedwindowt-class.md)实现控件的类数据成员。 它还添加了消息映射和消息处理程序函数来处理控件的 Windows 消息。 从列表中选择你想要创建，如果任何 Windows 控件的类型。  

  
-   `Button`  
  
-   `ListBox`  
  
-   `SysAnimate32`  
  
-   `SysListView32`  
  
-   `ComboBox`  
  
-   `RichEdit`  
  
-   `SysDateTimePick32`  
  
-   `SysMonthCal32`  
  
-   `ComboBoxEx32`  
  
-   `ScrollBar`  
  
-   `SysHeader32`  
  
-   `SysTabControl32`  
  
-   `Edit`  
  
-   `Static`  
  
-   `SysIPAddress32`  
  
-   `SysTreeView32`  
  
 **杂项状态**  
 设置控件的其他外观和行为选项。  
  
-   **在运行时不可见**： 设置要在运行时不可见的控件。 不可见的控件可用于在后台，如触发事件以固定的间隔执行操作。  
  
-   **作用类似按钮**： 集`OLEMISC_ACTSLIKEBUTTON`中位[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)枚举，以启用控件用作喜欢按钮。 如果容器已标记为默认按钮的控件的客户端站点，则选择此选项可启用按钮控件，以显示本身为默认按钮用较粗的框架绘制自身。 请参阅[CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)有关详细信息。  
  
-   **标签可以充当**： 集`OLEMISC_ACTSLIKELABEL`中位`OLEMISC`枚举，以允许将容器的本机标签控件。 容器确定应如何处理此标志，如果任何内容。  
  
 **其他**  
 设置控件的其他行为选项。  
  
-   **规范化 DC**： 设置的控件进行调用以绘制自身时，创建规范化的设备上下文。 此操作标准化控件的外观，但它使绘制效率较低。  
  
-   **仅适用于窗口**： 指定你的控件不能为无窗口。 如果不选择此选项，你控件是自动支持无窗口对象的容器中无窗口，它是自动为有窗口不支持无窗口对象的容器中。 选择此选项将强制控件为有窗口的即使在支持无窗口对象的容器。  
  
-   **可插入**： 选择此选项以使控件出现在**插入对象**Word 和 Excel 等应用程序对话框。 然后可以由任何应用程序支持通过此对话框中的嵌入的对象插入您的控件。  
  
## <a name="see-also"></a>请参阅  
 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT 示例： 超类标准 Windows 控件](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)

