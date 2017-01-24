---
title: "编译器警告（等级 1）C4612 | Microsoft Docs"
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
  - "C4612"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4612"
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4612
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含文件名中有错误  
  
 当文件名不正确或缺失时，此警告与 **\#pragma include\_alias**一起出现。  
  
 **\#pragma include\_alias** 语句的参数可使用引号形式（**"***文件名***"**）或尖括号形式（**\<***文件名***\>**），但两者必须使用相同的形式。  
  
## 示例  
  
```  
// C4612.cpp // compile with: /W1 /LD #pragma include_alias("StandardIO", <stdio.h>) // C4612  
```