---
title: "错误 C1092 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1092"
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“编辑并继续”不支持对数据类型的更改；需要生成  
  
 自上次成功生成后更改或添加了数据类型。  
  
-   “编辑并继续”不支持更改现有数据类型（包括类、结构或枚举定义）。  必须停止调试并生成应用程序。  
  
-   如果程序数据库文件是只读的，如 vc*x*0.pdb（此处 *x* 是使用中的 Visual C\+\+ 的主要版本），则“编辑并继续”不支持添加新数据类型。  要添加数据类型，编译器必须以写模式打开 .pdb 文件。  
  
### 移除该错误但不结束当前的调试会话  
  
1.  将数据类型更改回出错前的状态。  
  
2.  从**“调试”**菜单中选择**“应用代码更改”**。  
  
### 若要移除该错误而不更改源代码  
  
1.  从**“调试”**菜单中选择**“停止调试”**。  
  
2.  从**“生成”**菜单中选择**“生成”**。  
  
 有关进一步的信息，请参见[受支持的代码更改](../Topic/Supported%20Code%20Changes%20\(C++\).md)。