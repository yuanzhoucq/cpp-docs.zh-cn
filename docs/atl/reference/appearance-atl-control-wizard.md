---
title: "外观，ATL 控件向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.control.misc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 控件向导，外观"
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 外观，ATL 控件向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在此处插入“搜索结果”摘要。  
  
 使用此向导页标识控件的其他用户元素选项。  此页适用于在 [选项，ATL 控件向导](../../atl/reference/options-atl-control-wizard.md) 页上的**“控件类型”**下被标识为**“标准控件”**的控件。  
  
## UIElement 列表  
 **视图状态**  
 设置容器内的控件外观。  
  
-   **“不透明”**：设置 [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) 枚举中的 `VIEWSTATUS_OPAQUE` 位并绘制传递到 [CComControlBase::OnDraw](../Topic/CComControlBase::OnDraw.md) 方法的整个控件矩形。  控件以完全不透明的形式显示，控件边界的背后不显示容器的任何部分。  
  
     该设置有助于容器更快地绘制控件。  如果没有选定此选项，则控件可以包含透明部分。  
  
     只有不透明的控件可以有纯色背景。  
  
-   设置 `VIEWSTATUS` 枚举中的 `VIEWSTATUS_SOLIDBKGND` 位。  控件的背景以没有图案的纯色显示。  
  
     只有同样选定**“不透明”**选项时，此选项才可用。  
  
 **添加的控件基于**  
 通过向实现控件的类添加 [CContainedWindow](../Topic/CContainedWindow.md) 数据成员来设置基于 Windows 控件类型的控件。  还添加消息映射和消息处理函数来处理控件的 Windows 消息。  从下表中选择要创建的 Windows 控件类型（如果有）。  
  
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
  
 **其他状态**  
 为控件设置其他外观和行为选项。  
  
-   **“运行时不可见”**：设置控件，使其在运行时不可见。  可使用不可见的控件在后台执行操作，例如以固定的间隔引发事件。  
  
-   **“行为像按钮”**：设置 [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) 枚举中的 `OLEMISC_ACTSLIKEBUTTON` 位，使控件的行为像按钮一样。  如果容器已将控件的客户端标记为默认按钮，选择此选项可使按钮 \(Button\) 控件能够用较粗的框架绘制自身，从而将自己显示为默认按钮。  有关更多信息，请参见[CComControlBase::GetAmbientDisplayAsDefault](../Topic/CComControlBase::GetAmbientDisplayAsDefault.md)。  
  
-   **“行为像标签”**：设置 `OLEMISC` 枚举中的 `OLEMISC_ACTSLIKELABEL` 位，使控件能够替换容器的本机标签。  容器确定如何处理此标志（如果有）。  
  
 **其他**  
 为控件设置其他行为选项。  
  
-   **“正常化的 DC”**：设置控件在被调用以绘制自身时，创建正常化的设备上下文。  该操作标准化控件的外观，但使绘制效率较低。  
  
-   **“仅为窗口”**：指定控件不能是无窗口的。  如果不选择此选项，则在支持无窗口对象的容器中，控件自动为无窗口；在不支持无窗口对象的容器中，控件自动为有窗口的。  选择此选项将强制控件为有窗口的，即使是在支持无窗口对象的容器中。  
  
-   **“可插入”**：选择此选项使控件出现在 Word 和 Excel 这类应用程序的**“插入对象”**对话框中。  控件于是可由支持嵌入对象的任何应用程序通过此对话框插入。  
  
## 请参阅  
 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT Sample: Superclasses a Standard Windows Control](http://msdn.microsoft.com/zh-cn/30e46bdc-ed92-417c-b6b8-359017265a7b)