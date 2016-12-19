---
title: "如何：添加功能区控件和事件处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "事件处理程序, 添加"
  - "功能区控件, 添加"
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：添加功能区控件和事件处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

功能区控件是元素，如按钮和组合框，添加到面板中。  面板是显示一组相关控件功能区栏的区域。  
  
 在本主题中，您将打开功能区设计器，添加按钮，然后链接该的事件显示“Hello World”。  
  
### 打开功能区设计器  
  
1.  在 Visual Studio 中，在 **视图** 菜单上，单击 **资源视图**。  
  
2.  在 **资源视图**中，双击功能区资源的设计图面上查看它。  
  
### 添加按钮和事件处理程序  
  
1.  在 **工具栏**中，单击 **按钮** 并将其拖动到设计图面的面板。  
  
2.  右键单击按钮，然后单击 **添加事件处理程序**。  
  
3.  在 **事件处理程序向导**中，确认 **添加编辑 \(A\)**默认设置并单击。  有关详细信息，请参阅[事件处理程序向导](../ide/event-handler-wizard.md)。  
  
4.  在代码编辑器中，将以下代码添加到该处理程序函数：  
  
    ```  
    MessageBox((LPCTSTR)L"Hello World");  
    ```  
  
## 请参阅  
 [RibbonGadgets 示例：功能区小工具应用程序](../top/visual-cpp-samples.md)   
 [功能区设计器 \(MFC\)](../mfc/ribbon-designer-mfc.md)