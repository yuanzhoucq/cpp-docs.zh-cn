---
title: "C 抽象声明符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ae6f7ca131e30c179d556e225600243500ae9379
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="c-abstract-declarators"></a>C 抽象声明符
抽象声明符是没有标识符的声明符，由一个或多个指针、数组或函数修饰符组成。 指针修饰符 (\*) 始终在声明符中的标识符前面；数组 ([ ]) 和函数 ( ( ) ) 修饰符紧跟在标识符后面。 了解这种情况后，您可以确定标识符将在抽象声明符中显示的位置并相应地解释声明符。 有关复杂声明符的其他信息和示例，请参阅[解释更复杂的声明符](../c-language/interpreting-more-complex-declarators.md)。 通常 `typedef` 可用于简化声明符。 请参阅 [Typedef 声明](../c-language/typedef-declarations.md)。  
  
 抽象声明符可能很复杂。 复杂的抽象声明符中的括号指定一个特定的解释，正如它们为声明中的复杂声明符所做的一样。  
  
 以下示例阐释了抽象声明符：  
  
```  
int *         // The type name for a pointer to type int:  
  
int *[3]      // An array of three pointers to int  
  
int (*) [5]   // A pointer to an array of five int  
  
int *()       // A function with no parameter specification  
              // returning a pointer to int  
  
// A pointer to a function taking no arguments and   
// returning an int  
  
int (*) ( void )    
  
// An array of an unspecified number of constant pointers to   
// functions each with one parameter that has type unsigned int   
// and an unspecified number of other parameters returning an int   
  
int (*const []) ( unsigned int, ... )  
```  
  
> [!NOTE]
>  不允许使用由一组空括号 ( ) 组成的抽象声明符，因为它的意义不明确。 无法确定隐含标识符是位于括号内（此时它是未修改类型）还是括号前（此时它是函数类型）。  
  
## <a name="see-also"></a>另请参阅  
 [声明符和变量声明](../c-language/declarators-and-variable-declarations.md)