---
title: "编译器警告（等级 1）C4655 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4655"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4655"
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4655
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**“**   
 ***symbol* ”：从最后生成以来，变量类型是新的，或在其他地方以不同的方式定义**  
  
 自上次成功生成后你更改或添加了新的数据类型。 “编辑并继续”不支持对现有数据类型的更改。  
  
 此警告后跟[错误 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 有关详细信息，请参阅[受支持的代码更改](../Topic/Supported%20Code%20Changes%20\(C++\).md)。  
  
### 若要在不结束当前调试会话的情况下删除此警告  
  
1.  将数据类型改回其在发生错误前的状态。  
  
2.  在“调试”菜单中选择“应用代码更改”。  
  
### 若要在不更改源代码的情况下删除此警告  
  
1.  在“调试”菜单上，选择“停止调试”。  
  
2.  在“生成”菜单上，选择“生成”。