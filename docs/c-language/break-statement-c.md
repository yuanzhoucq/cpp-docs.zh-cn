---
title: "break 语句 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: break
dev_langs: C++
helpviewer_keywords: break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a180c88fc71e4786e8512bc26421825132611ed4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="break-statement-c"></a>break 语句 (C)
`break` 语句将终止执行其所在位置最接近的外围 `do`、`for`、`switch` 或 `while` 语句。 控制权将传递给已终止语句后面的语句。  
  
## <a name="syntax"></a>语法  
 *jump-statement*:  
 `break;`  
  
 `break` 语句通常用于终止 `switch` 语句中的特定用例的处理。 缺少外围的迭代或 `switch` 语句会引发错误。  
  
 在嵌套语句中，`break` 语句只终止直接包围它的 `do`、`for`、`switch` 或 `while` 语句。 可以在嵌套结构外部的其他地方使用 `return` 或 `goto` 语句来移交控制权。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [break 语句](../cpp/break-statement-cpp.md)