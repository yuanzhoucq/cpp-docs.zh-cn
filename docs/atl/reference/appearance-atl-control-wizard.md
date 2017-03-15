---
title: "外观、 ATL 控件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.misc
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: 12
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: dde27a7b62f3ee3b5fe8fcacd8141e9f89ed3c98
ms.lasthandoff: 02/24/2017

---
# <a name="appearance-atl-control-wizard"></a>外观，ATL 控件向导
在此处插入摘要的"搜索结果"。  
  
 向导的此页用于识别该控件的其他用户元素选项。 此页才可用的控件标识为**标准控件**下**控件类型**上[选项、 ATL 控件向导](../../atl/reference/options-atl-control-wizard.md)页。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **查看状态**  
 设置容器内控件的外观。  
  
-   **不透明**︰ 集`VIEWSTATUS_OPAQUE`中位[VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)枚举和绘制整个控件矩形传递给[CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法。 此控件显示完全不透明，并容器的任何控件边界的背后显示。  
  
     此设置有助于更快地绘制控件的容器。 如果未选择此选项，该控件可以包含透明部分。  
  
     只有不透明的控件可以显示纯背景色。  
  
-   集`VIEWSTATUS_SOLIDBKGND`中位`VIEWSTATUS`枚举。 控件的背景显示为具有无模式的纯色。  
  
     此选项才可用才**不透明**还选择选项。  
  
 **将控件添加**  
 设置要通过添加基于 Windows 控件类型的控件[CContainedWindow](ccontainedwindowt-class.md)于实现该控件的类数据成员。 它还添加了消息映射和消息处理程序函数来处理该控件的 Windows 消息。 从列表中选择你想要创建，如果任何 Windows 控件的类型。  

  
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
 设置控件的其他外观和行为的选项。  
  
-   **在运行时不可见**︰ 设置控件，使其在运行时不可见。 不可见的控件可用于在后台，如触发事件以固定的间隔内执行操作。  
  
-   **像按钮**︰ 集`OLEMISC_ACTSLIKEBUTTON`中位[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)枚举值，用于使控件执行操作喜欢按钮。 如果容器已标记为默认按钮的控件的客户端，可选择此选项使按钮控件以将它用较粗的框架绘制自身显示为默认按钮。 请参阅[CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)有关详细信息。  
  
-   **像标签**︰ 集`OLEMISC_ACTSLIKELABEL`中位`OLEMISC`枚举值，用于使控件能够替换容器的本机标签。 容器确定如何处理此标志，如果任何内容。  
  
 **其他**  
 设置控件的其他行为选项。  
  
-   **正常化的 DC**︰ 设置控件被调用来绘制自身时，创建正常化的设备上下文。 此操作标准化控件的外观，但使绘制效率较低。  
  
-   **仅适用于窗口**︰ 指定您的控件不能处于无窗口状态。 如果不选择此选项，控件是自动支持无窗口对象的容器中无窗口，并自动为有窗口不支持无窗口对象的容器中。 选择此选项将强制控件为有窗口的即使在支持无窗口对象的容器。  
  
-   **可插入**︰ 选择此选项以使控件出现在**插入对象**Word 和 Excel 等应用程序对话框。 然后可以由任何应用程序支持通过此对话框中的嵌入的对象插入您的控件。  
  
## <a name="see-also"></a>另请参阅  
 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT 示例︰ 超类标准 Windows 控件](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)


