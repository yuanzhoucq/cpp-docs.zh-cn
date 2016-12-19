---
title: "编译器警告（等级 1）C4657 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4657"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4657"
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4657
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表达式涉及一种数据类型，该数据类型为自最后生成以来的新类型  
  
 你添加或更改了数据类型，使其成为自上次成功生成后的源代码中的新类型。 “编辑并继续”不支持对现有数据类型的更改。  
  
 此警告将始终后跟[错误 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 有关详细信息，请参阅[受支持的代码更改](../Topic/Supported%20Code%20Changes%20\(C++\).md)。  
  
### 若要在不结束当前调试会话的情况下删除此警告  
  
1.  将数据类型改回其在发生错误前的状态。  
  
2.  在“调试”菜单中选择“应用代码更改”。  
  
### 若要在不更改源代码的情况下删除此错误  
  
1.  在“调试”菜单上，选择“停止调试”。  
  
2.  在“生成”菜单上，选择“生成”。