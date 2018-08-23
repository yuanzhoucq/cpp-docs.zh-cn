---
title: Null 语句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab391bb75dd6e7a2ef1ccf0951fa93770e6cd316
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408772"
---
# <a name="null-statement"></a>Null 语句
"Null 语句"是的表达式语句*表达式*缺失。 当语言的语法调用语句而不是表达式计算时，它很有用。   它包括分号。  
  
 Null 语句通常用作迭代语句中的占位符或用作在复合语句或函数的末尾放置标签的语句。  
  
 以下代码片段说明如何将一个字符串复制到另一个字符串，并包含 null 语句：  
  
```cpp 
// null_statement.cpp  
char *myStrCpy( char *Dest, const char *Source )  
{  
    char *DestStart = Dest;  
  
    // Assign value pointed to by Source to  
    // Dest until the end-of-string 0 is  
    // encountered.  
    while( *Dest++ = *Source++ )  
        ;   // Null statement.  
  
    return DestStart;  
}  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [表达式语句](../cpp/expression-statement.md)