---
title: "将消息映射到函数 | Microsoft Docs"
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
  - "vc.codewiz.mapping.msg.function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "消息映射 [C++], 将消息映射到函数"
  - "Windows 消息 [C++], 添加消息处理程序"
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 将消息映射到函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“属性”窗口使您能够将消息处理程序（MFC 用户界面类的成员函数）绑定到应用程序资源生成的消息。  它们使用 [MFC 消息映射](../../mfc/messages-and-commands-in-the-framework.md)创建绑定。  
  
 使用“类视图”创建从某个框架类导出的新类时，它自动将完整的功能类放在指定的头文件 \(.h\) 和实现文件 \(.cpp\) 中。  
  
> [!NOTE]
>  若要添加不处理消息的新类，请在文本编辑器中直接创建该类。  
  
### 用“属性”窗口定义或移除消息处理程序  
  
1.  在“类视图”中，单击该类。  
  
2.  在“属性”窗口中，单击“消息”按钮。  
  
    > [!NOTE]
    >  在“类视图”中选择类名或者在源窗口中单击时，“消息”按钮可用。  
  
     如果项目有消息处理程序，处理程序的名称将出现在右列中消息的旁边。  
  
3.  如果消息没有处理程序，则在“属性”窗口中单击右列中的单元格以将建议的处理程序名称显示为 \<\<添加\>\>*HandlerName*。（例如，`WM_TIMER` 消息处理程序建议\<添加 \>`OnTimer`）。  
  
4.  单击建议的名称以添加该函数的存根 \(stub\) 代码。  
  
5.  若要编辑消息处理程序，请在“类视图”中双击消息并在源窗口中编辑代码。  
  
 若要移除消息处理程序，请在右列中双击处理程序并选择\<删除\>*HandlerName*。  函数的代码被注释掉。  
  
## 请参阅  
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Adding Event Handlers for Dialog Box Controls](../../mfc/adding-event-handlers-for-dialog-box-controls.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)