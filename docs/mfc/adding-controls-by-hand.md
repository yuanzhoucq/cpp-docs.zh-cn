---
title: "手动添加控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "公共控件 [C++], 添加"
  - "控制输入焦点"
  - "控件 [MFC], 添加到对话框"
  - "对话框控件 [C++], 添加到对话框"
  - "焦点, 控制输入"
  - "输入焦点控制"
  - "Windows 公共控件 [C++], 添加"
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 手动添加控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以 [将控件添加到对话框编辑器中的对话框。](../mfc/using-the-dialog-editor-to-add-controls.md) 或添加自己，它们用代码。  
  
 若要创建控件对象，通常将会嵌入在 .c. C\+\+ 对话框或框架窗口对象的 C\+\+ 控件对象。  与框架中的许多其他对象，则控件需要构造两个阶段。  在创建父对话框或框架窗口的一部分，则应调用控件的 **创建** 成员函数。  对于对话框，这通常可以在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)以及框架窗口，在 [OnCreate](../Topic/CWnd::OnCreate.md)。  
  
 下面的示例演示声明在派生的对话框类的类声明的一个 `CEdit` 对象并调用 `OnInitDialog`的 **创建** 成员函数。  由于其中声明 `CEdit` 对象作为嵌入对象，它自动构造，当构造对话框对象时，但仍必须初始化它与自己的 **创建** 成员函数。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/CPP/adding-controls-by-hand_1.h)]  
  
 以下 `OnInitDialog` 函数用于设置矩形，然后调用 **创建** 创建 Windows 编辑控件并将其附加到未初始化的 `CEdit` 对象。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/CPP/adding-controls-by-hand_2.cpp)]  
  
 在创建对象之后编辑，还可以设置项指向控件通过调用 `SetFocus` 成员函数。  最后，将返回 0。`OnInitDialog` 表示形式，因此设置焦点。  如果返回非零值，则对话框管理器设置焦点设置在对话框项列表中的第一个控件的项。  在许多情况下，您需要将控件添加带有对话框编辑器中的对话框。  
  
## 请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)   
 [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)