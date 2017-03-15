---
title: "重写虚函数 (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.virtualfunc.override"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基类, 重写虚函数定义"
  - "“属性”窗口, 重写虚函数"
  - "虚函数, 重写"
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 重写虚函数 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以从 Visual Studio[“属性”窗口](../Topic/Properties%20Window.md)中重写在基类中定义的虚函数。  
  
### 在“属性”窗口中重写虚函数  
  
1.  在“类视图”中，单击该类。  
  
2.  在“属性”窗口中，单击**“重写”**按钮。  
  
    > [!NOTE]
    >  在类视图中选择类名或在源窗口中单击时，将提供**“重写”**按钮。  
  
     左列列出虚函数。  如果虚函数的名称也出现在右列中，则已实现重写。  
  
3.  如果函数没有重写，则在“属性”窗口中单击右列中的单元格，将建议的函数重写名称显示为 \<add\>*FuncName*。  
  
4.  单击建议的名称以添加该函数的存根 \(stub\) 代码。  
  
5.  若要编辑重写函数，请在“类视图”中双击函数名并在源窗口中编辑代码。  
  
 若要移除重写，请在右列中单击重写函数名并选择 \<删除\>*FuncName*。  函数的代码被注释掉。  
  
## 请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)