---
title: "编译器警告（等级 1）C4138 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4138"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4138"
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4138
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在注释外找到“\*\/”  
  
 结束注释分隔符前面没有开始注释分隔符。 编译器将假定星号 \(**\***\) 和正斜杠 \(\/\) 之间留有一个空格。  
  
## 示例  
  
```  
// C4138a.cpp // compile with: /W1 int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning int main() { }  
```  
  
 此警告可由嵌套注释引起。  
  
 如果注释掉包含注释的代码段，在 **\#if \/ \#endif** 块中包含代码，并将控制表达式设置为零，可能会解决此警告：  
  
```  
// C4138b.cpp // compile with: /W1 #if 0 int my_variable;   /* Declaration currently not needed */ #endif int main() { }  
```