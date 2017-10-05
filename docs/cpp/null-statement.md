---
title: "Null 语句 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: f15fda458fe604d0501c4daa87e6a76cd0422260
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="null-statement"></a>Null 语句
"Null 语句"是使用表达式语句*表达式*缺少。 当语言的语法调用语句而不是表达式计算时，它很有用。   它包括分号。  
  
 Null 语句通常用作迭代语句中的占位符或用作在复合语句或函数的末尾放置标签的语句。  
  
 以下代码片段说明如何将一个字符串复制到另一个字符串，并包含 null 语句：  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
 [表达式语句](../cpp/expression-statement.md)
