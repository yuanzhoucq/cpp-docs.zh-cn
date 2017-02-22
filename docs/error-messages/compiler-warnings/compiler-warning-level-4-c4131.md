---
title: "编译器警告（等级 4）C4131 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4131"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4131"
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 4）C4131
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“函数”：使用旧样式的声明符  
  
 指定的函数声明不是原型形式。  
  
 旧样式的函数声明应转换为原型形式。  
  
 下面的示例展示一个旧样式的函数声明：  
  
```  
// C4131.c // compile with: /W4 /c void addrec( name, id ) // C4131 expected char *name; int id; { }  
```  
  
 下面的示例展示一个原型形式：  
  
```  
void addrec( char *name, int id ) { }  
```