---
title: "MFC ActiveX 控件：创建 Windows 控件的子类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "precreatewindow"
  - "IsSubclassed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoSuperclassPaint 方法"
  - "IsSubclassed 方法"
  - "MFC ActiveX 控件, 创建"
  - "MFC ActiveX 控件, 子类控件"
  - "OnDraw 方法, MFC ActiveX 控件"
  - "PreCreateWindow 方法, 重写"
  - "反映的消息, 在 ActiveX 控件中"
  - "创建子类"
  - "创建 Windows 控件的子类"
  - "创建子类, Windows 控件"
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC ActiveX 控件：创建 Windows 控件的子类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍了子类化通用窗口控件来创建 ActiveX 控件的过程。  子类化现有的Windows 控件，是一种快速开发的 ActiveX 控件。  新的控件将具有这些窗口控件的能力，比如绘制和响应鼠标点击。  MFC ActiveX 工具控件是 [按钮](../top/visual-cpp-samples.md) 子类化窗口的控件示例。  
  
 创建窗口控件的子类，完成以下任务：  
  
-   [重写 COleControl中的 IsSubclassedControl 和 PreCreateWindow 成员函数](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [修改 OnDraw 成员函数](#_core_modifying_the_ondraw_member_function)  
  
-   [处理所有会反映到控件的ActiveX控件消息 \(OCM\)](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  如果使用 **控件设置** 中的 **Select Parent Window Class** 大部分工作都会由 ActiveX 控件向导帮您做好了。  
  
 更多有关子类化控件的详细信息，请参阅知识库文章Q243454。  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> 重写 IsSubclassedControl 和 PreCreateWindow  
 若要重写 `PreCreateWindow` 和 `IsSubclassedControl`，请向控件类的声明部分添加以下代码 `protected` 。  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 在控件实现文件 \(.cpp\) 中，添加以下代码实现两个函数的重写：  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 请注意，在此示例中，窗口按钮控件在 `PreCreateWindow`中指定。  但是，所有标准 Windows 控件都可以创建子类。  更多有关标准 Windows 控件的详细信息，请参见 [控件](../mfc/controls-mfc.md)。  
  
 当子类化窗口控件时，您可能希望在创建控件的窗口时，指定特定窗口样式 \(**WS\_**\) 或扩展窗口样式 \(**WS\_EX\_**\) 标志。  您可以修改 **cs.style** 和 **cs.dwExStyle** 结构字段来设置这些参数在 `PreCreateWindow` 成员函数中的值。  对这些字段的修改，应当使用 `OR` 操作，这样可以让由 `COleControl`类设置的默认标记得到保留。  例如，如果控件按钮控件的子类，您又希望控件可以作为复选框，那么在 `CSampleCtrl::PreCreateWindow`的实现中，返回语句之前，插入以下代码：  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 此运算可以加入**BS\_CHECKBOX** 标志样式，同时在`COleControl`类中的默认样式标志 \(**WS\_CHILD**\) 也完整保留。  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a> 修改 OnDraw 成员函数  
 如果您需要您的子类控件与相应的Windows控件保持相同的外观，控件的成员函数`OnDraw` 只应包含调用 `DoSuperclassPaint` 成员函数，如下面的示例所示：  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 `DoSuperclassPaint` 成员函数，由 `COleControl`实现，在指定的设备上下文中，使用 Windows 控件的窗口过程，在边框内绘制控件。  这样使控件即使处于不活动状态，也是可见的。  
  
> [!NOTE]
>  `DoSuperclassPaint` 成员函数仅仅在这种控制类型下起作用，这种类型允许设备上下文用`WM_PAINT` 消息的 **wParam** 来传递。  这包含某些标准 Windows 控件，例如 **SCROLLBAR** 以及 **BUTTON**和所有常用控件。  对于不支持此行为的控件，则必须自己编写代码来正确地显示非活动控件。  
  
##  <a name="_core_handling_reflected_window_messages"></a> 处理反射的Window消息  
 Windows 控件通常将某些 Window 信息发送到其父窗口。  其中一些消息有， 比如**WM\_COMMAND**提供用户操作的通知。  其他消息，比如 `WM_CTLCOLOR`用于获取来自父窗口的信息。  ActiveX 控件与父窗口的通信通常通过其他方式完成。  通知通过引发事件来发送 \(发送事件通知\)，因此，有关控件的信息容器是通过访问容器的环境属性来获取的。  由于这些通信方法存在，ActiveX 控件容器不应该处理任何由控件发送的窗口信息。  
  
 若要阻止容器接收由子类Windows控件发送的 Window 消息，`COleControl` 创建了一个额外的窗口充当控件的父级。  此额外的窗口，称为“反射器”，仅为Windows控件的子类和与控件窗口有相同大小位置的ActvieX 控件所创建。  反射器窗口截获某些 Windows 消息并将其发送回控件。  控件，在窗口过程，可以通过对 ActiveX 控件 采取适当的操作\(例如，事件触发\)来处理这些反射消息。  对于被截取的窗口消息和它们相对应的反射消息列表参见 [反映的窗口消息 ID](../mfc/reflected-window-message-ids.md)。  
  
 ActiveX 控件容器被设计为执行反射消息，就无需为 `COleControl` 创建反射器窗口，这样缩小了子类窗口的控件运行时系统开销。  `COleControl` 通过检查 MessageReflect 环境属性的 **TRUE**来检测容器是否有这个能力。  
  
 若要处理一个反映的窗口消息，请在控件消息映射中添加一个条目，并实现处理函数。  由于反射消息不是由Windows定义的标准的消息集，类视图尚未支持添加这样的消息处理程序。  然而，手动添加处理程序并不很困难。  
  
 要添加反射的窗口消息的消息处理程序，需要手动执行以下步骤：  
  
-   在控件类.H 文件中声明处理程序函数。  函数的返回值类型为 **LRESULT** ，两个参数的类型分别为 **WPARAM** 和 **LPARAM**。  例如：  
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   在控件类 .cpp 文件中，将 `ON_MESSAGE` 项添加到消息映射中。  此项的参数应该是消息标示符和处理函数的名称。  例如：  
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   在 .cpp 文件，请还要实现成员函数 **OnOcmCommand** 来处理反射消息。  **wParam** 和 **lParam** 参数与原始窗口消息中的相同。  
  
 更多关于涉及到MFC ActiveX 工具控件的反射消息如何处理 ，请参见 [BUTTON](../top/visual-cpp-samples.md)。  它阐明了一个用**BN\_CLICKED** 检测通知代码并通过点击事件触发相应的 **OnOcmCommand**处理程序。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)