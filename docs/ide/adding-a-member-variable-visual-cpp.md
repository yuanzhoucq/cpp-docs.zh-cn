---
title: "添加成员变量 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.classes.member.variable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "成员变量"
  - "成员变量, 添加"
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 添加成员变量 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用“类视图”将成员变量添加到类。  成员变量可用于[数据交换和数据验证](../mfc/dialog-data-exchange-and-validation.md)或者可以是一般性的。  数据成员变量向导是专门为获取相关信息并利用这些信息在源文件中的适当位置插入元素而设计的。  可以从[资源视图](../windows/resource-view-window.md)中的[对话框编辑器](../mfc/dialog-editor.md)或从[“类视图”](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中添加成员变量。  
  
> [!NOTE]
>  当设计和实现对话框时，如果先使用对话框编辑器添加对话框控件，然后再实现这些控件的成员变量，则效率可能会更高。  
  
### 使用“添加成员变量向导”在“资源视图”中添加对话框控件的成员变量  
  
1.  在“资源视图”中，展开项目节点和对话框节点以显示项目的对话框列表。  
  
2.  双击要将成员变量添加到的对话框，在对话框编辑器中打开它。  
  
3.  在对话框编辑器中显示的对话框中，右击要将成员变量添加到的控件。  
  
4.  在快捷菜单上，单击**“添加变量”**显示[“添加成员变量向导”](../ide/add-member-variable-wizard.md)。  
  
    > [!NOTE]
    >  **Control ID** 中已提供了一个默认值。  
  
5.  在适当的向导框中提供信息。  有关更多信息，请参见[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)。  
  
6.  单击“完成”向项目添加定义和实现代码并关闭向导。  
  
### 使用“添加成员变量向导”从“类视图”中添加成员变量  
  
1.  在[“类视图”](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，展开项目节点以显示项目中的类。  
  
2.  右击要将变量添加到的类。  
  
3.  在快捷菜单上，单击**“添加”**，然后单击**“添加变量”**显示“添加成员变量向导”。  
  
4.  在适当的向导框中提供信息。  有关详细信息，请参见[添加成员变量向导](../ide/add-member-variable-wizard.md)。  
  
5.  单击“完成”向项目添加定义和实现代码并关闭向导。  
  
## 请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)