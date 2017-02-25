---
title: "Null 语句 (C) | Microsoft Docs"
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
  - "表达式 [C++], null"
  - "null 语句"
  - "null 值, 表达式"
  - "分号, C null 语句"
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Null 语句 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“null 语句”是仅包含分号的语句；它可在需要语句时显示。  执行 null 语句时不会发生任何事件。  编码 null 语句的正确方式是：  
  
## 语法  
  
```  
  
;  
  
```  
  
## 备注  
 **do**、**for**、**if** 和 `while` 等语句需要可执行语句显示为语句体。  在无需实质性语句体的情况下，null 语句可满足语法要求。  
  
 与任何其他 C 语句一起使用时，您可在 null 语句前包含一个标签。  若要标记某个不是语句的项（如复合语句的右大括号），您可标记一个 null 语句并紧靠该项的前面插入该语句以取得相同的效果。  
  
 以下示例阐释了 null 语句：  
  
```  
for ( i = 0; i < 10; line[i++] = 0 )  
     ;  
```  
  
 在此示例中，**for** 语句 `line[i++] = 0` 的循环表达式将 `line` 的前 10 个元素初始化为 0。  由于无需任何其他语句，因此语句体为 null 语句。  
  
## 请参阅  
 [语句](../c-language/statements-c.md)