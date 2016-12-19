---
title: "在您的应用程序中使用属性表 | Microsoft Docs"
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
  - "AddPage 方法"
  - "CPropertyPage 类, 样式"
  - "Create 方法 [C++], 属性表"
  - "对话框资源"
  - "对话框模板, 属性表"
  - "DoModal 方法属性表"
  - "属性页, 属性表"
  - "属性表, 关于属性表"
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在您的应用程序中使用属性表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要在应用程序中使用属性表，请完成以下步骤：  
  
1.  为每页属性页创建对话框模板资源。  记住用户可能从一页切换到另一个，因此，尽量一致布置致每个页。  
  
     所有页的对话框模板不必具有相同的大小。  框架使用最大的页的大小确定在属性页的属性表分配的空格数。  
  
     当你为资源页面创建对话框模板资源时，必须在对话框属性表必须指定以下样式：  
  
    -   设置 **标题** 编辑框在 **常规** 页到希望显示此页上的选项卡的文本。  
  
    -   设置 **样式** 列表框在 **样式** 页 **Child**。  
  
    -   将在 **样式** 页上的 **边框** 列表框设置为 **细**。  
  
    -   确保选上了在 **样式** 页中的 **Titlebar** 复选框。  
  
    -   确保选上了在 **更多样式** 页中的 **Disabled** 复选框。  
  
2.  创建一个 [CPropertyPage](../mfc/reference/cpropertypage-class.md)对应于每个属性页对话框模板的派生类。  参阅 [添加类](../ide/adding-a-class-visual-cpp.md)。  选择 `CPropertyPage` 作为基类。  
  
3.  创建成员变量表示此属性页的值。  增加成员变量到属性页上的进程与添加成员变量到对话框是一样的，因为一个属性页面是一个特定的对话框。  有关更多信息，请参见 [定义对话框控件的成员变量](../mfc/defining-member-variables-for-dialog-controls.md)。  
  
4.  在源代码中构造一个 [CPropertySheet](../mfc/reference/cpropertysheet-class.md) 对象。  通常，在命令的处理程序中构造 `CPropertySheet` 对象显示属性表。  此对象表示整个属性表。  如果创建带有 [DoModal](../Topic/CPropertySheet::DoModal.md) 函数的模式属性表，框架提供三个命令按钮默认方法：好，取消，和应用。  框架创建用 [创建](../Topic/CPropertySheet::Create.md) 函数创建的无模式属性表的命令按钮。  不需要从 `CPropertySheet` 派生一个类，除非希望添加其他控件 \(如窗口预览\) 或显示无模式属性表。  此步骤为非模式属性表是必需的，因为这些可能不包含用于关闭属性表的任何默认控件。  
  
5.  对于将添加到属性表的每个页，请执行以下操作：  
  
    -   在此过程前面创建，为每个 `CPropertyPage` 派生类构造一个对象。  
  
    -   为每页调用 [CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md)。  
  
     通常，创建 `CPropertySheet` 对象在该步骤中也创建 `CPropertyPage` 对象。  但是，如果要实现一个 `CPropertySheet`派生类，则可以将 `CPropertySheet` 对象嵌入在 `CPropertyPage` 对象并从 `CPropertySheet`派生类构造函数调用每页的 `AddPage` 。  `AddPage` 向页的属性列表添加 `CPropertyPage` 对象，但实际上不为该页创建窗口。  因此，直到属性表窗口创建调用 `AddPage`，等待才是有必须的；您可以从属性表的构造函数调用 `AddPage`。  
  
     默认情况下，如果属性表比属性表的单个行具有更多选项卡，则选项卡将多行堆叠。  禁用堆叠，使用参数的调用 [CPropertySheet::EnableStackedTabs](../Topic/CPropertySheet::EnableStackedTabs.md) 将其设置为 **FALSE**。  当创建表属性时，必须调用 `EnableStackedTabs`。  
  
6.  调用 [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md) 或 [创建](../Topic/CPropertySheet::Create.md) 显示属性表。  调用 `DoModal` 创建属性表作为模式对话框。  调用 **创建** 创建属性表用作无模式对话框。  
  
7.  在属性页和属性表的所有者的之间交换数据。  这将在文章 [交换数据](../mfc/exchanging-data.md) 中解释。  
  
 有关如何使用属性表的示例，请参阅 MFC 泛型示例 [PROPDLG](../top/visual-cpp-samples.md)。  
  
## 请参阅  
 [属性表](../mfc/property-sheets-mfc.md)