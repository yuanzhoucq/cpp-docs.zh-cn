---
title: "“对话框编辑器”选项卡，工具箱 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "工具箱 [C++]，“对话框编辑器”选项卡"
  - "控件 [C++]，类型"
  - "对话框中的 syslink 控件"
  - "自定义控件 [Visual Studio]，对话框"
  - "控件 [C++]，标准"
  - "对话框编辑器，创建控件"
  - "控件 [C++], 添加到对话框"
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “对话框编辑器”选项卡，工具箱
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用对话框编辑器时，对话框编辑器选项卡将出现在 [工具箱窗口](../Topic/Toolbox.md)中。 要将控件添加到新的对话框中，请将控件从工具箱拖动到正在创建的对话框中（有关详细信息，请参阅[将控件添加到对话框中](../mfc/adding-a-control-to-a-dialog-box.md)）。 然后，可以移动控件或更改其大小和形状。  
  
 工具箱中的可用标准控件包括：  
  
-   [Button 控件](../mfc/reference/cbutton-class.md)  
  
-   [复选框控件](../mfc/reference/button-styles.md)  
  
-   [组合框控件](../mfc/reference/ccombobox-class.md)  
  
-   [编辑控件](../mfc/reference/cedit-class.md)  
  
-   分组框  
  
-   [列表框控件](../mfc/reference/clistbox-class.md)  
  
-   [单选按钮控件](../mfc/reference/button-styles.md)  
  
-   [静态文本控件](../mfc/reference/cstatic-class.md)  
  
-   [图片控件](../mfc/reference/cpictureholder-class.md)  
  
-   [Rich Edit 2.0 控件](../mfc/using-cricheditctrl.md)  
  
-   [滚动条控件](../mfc/reference/cscrollbar-class.md)  
  
 应用程序里工具箱中的可用 [Windows 公共控件](../mfc/controls-mfc.md) 增强了功能性。 它们包括：  
  
-   [Slider 控件](../mfc/slider-control-styles.md)  
  
-   [数值调节钮控件](../mfc/using-cspinbuttonctrl.md)  
  
-   [进度控件](../mfc/styles-for-the-progress-control.md)  
  
-   [热键控件](../mfc/using-a-hot-key-control.md)  
  
-   [列表控件](../mfc/list-control-and-list-view.md)  
  
-   [树控件](../mfc/tree-control-styles.md)  
  
-   [Tab 控件](../mfc/tab-controls-and-property-sheets.md)  
  
-   [动画控件](../mfc/using-an-animation-control.md)  
  
-   [日期时间选择器控件](../mfc/creating-the-date-and-time-picker-control.md)  
  
-   [月历控件](../mfc/month-calendar-control-examples.md)  
  
-   [IP 地址控件](../mfc/reference/cipaddressctrl-class.md)  
  
-   [扩展组合框控件](../mfc/creating-an-extended-combo-box-control.md)  
  
-   [自定义控件](../mfc/custom-controls-in-the-dialog-editor.md)  
  
 可以通过选择工具箱中的**自定义控件**图标并将其拖放到对话框中的方法来向对话框中添加自定义控件。 要添加 Syslink 控件，请添加自定义控件，然后将控件的 **Class** 属性更改为 **Syslink**。 这将导致属性刷新并显示 Syslink 控件属性。 有关 MFC 包装器类的信息，请参阅 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)。  
  
 还可以[向对话框中添加 ActiveX 控件](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
 还可以自定义工具箱窗口以方便使用。 有关详细信息，请参阅[管理工具箱中的项目和选项卡](http://msdn.microsoft.com/zh-cn/21285050-cadd-455a-b1f5-a2289a89c4db)。 例如，可以在工具箱窗口中放置控件以方便访问。 有关详细信息，请参阅[自定义工具箱对话框](http://msdn.microsoft.com/zh-cn/bd07835f-18a8-433e-bccc-7141f65263bb)。  
  
 有关 RichEdit 1.0 控件使用 MFC 的详细信息，请参阅 [RichEdit 1.0 控件使用 MFC](../mfc/using-the-richedit-1-0-control-with-mfc.md)  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [控件](../mfc/controls-mfc.md)   
 [控件类](../mfc/control-classes.md)   
 [对话框类](../mfc/dialog-box-classes.md)   
 [滚动条样式](../mfc/reference/scroll-bar-styles.md)   
 [Rich Edit 控件示例](../mfc/rich-edit-control-examples.md)   
 [Adding Event Handlers for Dialog Box Controls](../mfc/adding-event-handlers-for-dialog-box-controls.md)   
 [对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)