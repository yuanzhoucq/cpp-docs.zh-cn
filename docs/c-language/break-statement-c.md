---
title: "break 语句 (C) | Microsoft Docs"
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
  - "break"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "break 关键字 [C]"
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# break 语句 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`break` 语句将终止执行其所在位置最接近的外围 `do`、`for`、`switch` 或 `while` 语句。  控制权将传递给已终止语句后面的语句。  
  
## 语法  
 *jump\-statement*：  
 `break;`  
  
 `break` 语句通常用于终止 `switch` 语句中的特定用例的处理。  缺少外围的迭代或 `switch` 语句会引发错误。  
  
 在嵌套语句中，`break` 语句只终止直接包围它的 `do`、`for`、`switch` 或 `while` 语句。  可以在嵌套结构外部的其他地方使用 `return` 或 `goto` 语句来移交控制权。  
  
 以下示例演示了 `break` 语句：  
  
```  
#include <stdio.h>  
int main() {  
   char c;  
   for(;;) {  
      printf_s( "\nPress any key, Q to quit: " );  
  
      // Convert to character value  
      scanf_s("%c", &c);  
      if (c == 'Q')  
          break;  
   }  
} // Loop exits only when 'Q' is pressed  
```  
  
## 请参阅  
 [break 语句](../cpp/break-statement-cpp.md)