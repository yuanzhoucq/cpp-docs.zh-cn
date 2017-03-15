---
title: "创建自己的对话框类 | Microsoft Docs"
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
  - "对话框 [C++], 创建"
  - "对话框类, 添加类向导"
  - "对话框类, 创建"
  - "文件 [C++], 创建"
  - "MFC 对话框, 创建"
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 创建自己的对话框类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于程序中每一对话框，请创建新对话框类与对话框资源一起使用。  
  
 [添加类](../ide/adding-a-class-visual-cpp.md) 解释如何创建新对话框类。  当创建了添加类向导时的对话框类，则编写在下面的项目。您指定的 H 和 .cpp 文件：  
  
 在。H 文件：  
  
-   对话框类的类声明。  类从派生。[CDialog](../mfc/reference/cdialog-class.md)  
  
 在 .cpp 文件：  
  
-   类的消息映射。  
  
-   对话框的标准构造函数。  
  
-   [DoDataExchange](../Topic/CWnd::DoDataExchange.md) 成员函数的重写。  编辑该函数。  对于对话框数据交换和验证功能。使用 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)面部分所述。  
  
## 请参阅  
 [使用代码向导创建对话框类](../mfc/creating-a-dialog-class-with-code-wizards.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)