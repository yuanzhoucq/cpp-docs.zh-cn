---
title: "函数原型 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea02b5b3bb1517623a0c3fc67a752d203f81c5a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="function-prototypes"></a>函数原型
函数声明位于函数定义之前，用来指定函数的名称、返回类型、存储类和其他特性。 若要作为原型，函数声明还必须为函数的参数确定类型和标识符。  
  
## <a name="syntax"></a>语法  
 `declaration`：  
 declaration-specifiers attribute-seq optinit-declarator-list opt;  
  
 /\* attribute-seq opt 是 Microsoft 专用的 */  
  
 *declaration-specifiers*：  
 storage-class-specifier declaration-specifiers opt  
  
 type-specifier declaration-specifiers opt  
  
 type-qualifier declaration-specifiers opt  
  
 *init-declarator-list*：  
 *init-declarator*  
  
 *init-declarator-list*  **,**  *init-declarator*  
  
 *init-declarator*：  
 *declarator*  
  
 declarator = initializer  
  
 `declarator`：  
 pointer optdirect-declarator  
  
 direct-declarator: /\* 函数声明符 \*/  
 direct-declarator  (  parameter-type-list  )  /* 新样式声明符 \*/  
  
 direct-declarator  (  identifier-list opt) /* 旧样式声明符 \*/  
  
 原型与函数定义具有相同的形式，只不过前者由紧跟在右括号后的分号结尾，因此没有主体。 在任一情况下，返回类型都必须与函数定义中指定的返回类型一致。  
  
 函数原型有下列重要用途：  
  
-   它们建立返回除 `int` 之外的类型的函数的返回类型。 尽管返回 `int` 值的函数不需要原型，但仍建议使用原型。  
  
-   如果没有完整原型，将进行标准转换，但不会尝试使用形参的数量检查实参的类型或数量。  
  
-   原型用于在定义函数之前初始化指向函数的指针。  
  
-   形参列表用于通过函数定义中的形参来检查函数调用中的实参的对应性。  
  
 每个形参的转换类型决定函数调用在堆栈上放置的实参的解释。 自变量和参数的类型不匹配可能导致堆栈上的自变量被错误解释。 例如，在 16 位计算机上，如果 16 位指针作为实参传递，然后声明为 long 形参，则堆栈上的前 32 位将解释为 long 形参。 此错误不仅会导致 long 参数出现问题，而且会导致其后面的所有参数出现问题。 您可通过声明所有函数的完整函数原型来检测此类错误。  
  
 原型将确定函数的特性，以便能检查位于函数定义前面（或者出现在其他源文件中）的函数调用是否存在参数类型和返回类型不匹配。 例如，如果在原型中指定 static 存储类说明符，则还必须在函数定义中指定 static 存储类。  
  
 完整参数声明 (`int a`) 可以与同一声明中的抽象声明符 (`int`) 组合在一起。 例如，以下声明是合法的：  
  
```  
int add( int a, int );  
```  
  
 原型可同时包含作为参数传递的每个表达式的类型和标识符。 但是，此类标识符的范围只到该声明的末尾。 原型也可以反映参数的数量是变量或未传递参数的事实。 如果没有此类列表，则不能显示不匹配项，从而使编译器无法生成有关它们的诊断消息。 有关类型检查的详细信息，请参阅[参数](../c-language/arguments.md)。  
  
 使用 /Za 编译器选项进行编译时，Microsoft C 编译器中的原型范围现在符合 ANSI。 这意味着，如果在原型中声明 `struct` 或 union 标记，则将在该范围而不是全局范围内输入该标记。 例如，为符合 ANSI 而使用 /Za 进行编译时，您绝不可能调用此函数而不遇到类型不匹配错误：  
  
```  
void func1( struct S * );  
```  
  
 若要更正代码，请在全局范围中函数原型之前定义或声明 `struct` 或 union：  
  
```  
struct S;  
void func1( struct S * );  
```  
  
 在 /Ze 下，仍将在全局范围内输入标记。  
  
## <a name="see-also"></a>请参阅  
 [函数](../c-language/functions-c.md)