---
title: "创建无模式属性表 | Microsoft Docs"
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
  - "Create 方法 [C++], 属性表"
  - "无模式属性表"
  - "属性表, 无模式"
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建无模式属性表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常，创建的属性表将有模式的。  当使用一模式属性表时，用户必须在使用应用程序的其他部分之前关闭属性表。  本文描述可使用创建无模式属性表允许用户保存打开，如果使用属性表应用程序的其他部分的方法。  
  
 显示属性表用作无模式对话框而不是作为模式对话框，而不是调用 [CPropertySheet::Create](../Topic/CPropertySheet::Create.md)[DoModal](../Topic/CPropertySheet::DoModal.md)。  必须还实现一些额外的任务支持无模式属性表。  
  
 其中一个是任务。它修改的属性表和外部对象之间交换数据属性表时打开。  这通常是与标准任务无模式对话框中。  此任务的一部分实现通信通道属性设置适用于的无模式属性表和外部对象的。  如果从无模式属性表，[CPropertySheet](../mfc/reference/cpropertysheet-class.md) 派生类此实现更加容易。  本文假定您这样做。  
  
 通信的方法的无模式属性表和外部对象 \(视图中当前选定之间例如，\) 将定义从属性表的指针到外部对象。  定义一个函数调用 \(类似于 `SetMyExternalObject`\)。`CPropertySheet`\- 更改指针的派生类，每当从外部对象的焦点更改为另一个架构。  `SetMyExternalObject` 函数需要重置属性设置每个页的以反映最近选择的外部对象。  为此，`SetMyExternalObject` 函数绑定可以访问 [CPropertyPage](../mfc/reference/cpropertypage-class.md) 属于 `CPropertySheet` 类的对象。  
  
 最方便的方式提供对在属性表中属性页将嵌入 `CPropertySheet`的 `CPropertyPage` 对象派生的对象。  嵌入 `CPropertyPage` 中 `CPropertySheet`对象派生的对象与模式对话框的典型方式不同，属性表的所有者创建 `CPropertyPage` 对象并将其传递给属性表通过 [CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md)。  
  
 具有确定的许多用户界面选择何时在应用非模式属性表设置的外部对象。  重写是应用当前属性页上的设置，只要用户更改任何值。  另一种方法是提供应用按钮，允许用户在提交之前累计在属性页上更改到外部对象。  有关方法处理应用按钮的信息，请参见 [处理应用按钮](../mfc/handling-the-apply-button.md)文章。  
  
## 请参阅  
 [属性表](../mfc/property-sheets-mfc.md)   
 [交换数据](../mfc/exchanging-data.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)