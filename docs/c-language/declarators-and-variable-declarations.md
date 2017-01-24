---
title: "声明符和变量声明 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "声明符, 定义"
  - "声明变量, 声明语句"
  - "声明变量, 声明符"
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 声明符和变量声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本节的其余部分描述了该列表中汇总的变量类型的声明的形式和含义。  具体来说，其余各节说明如何声明以下内容：  
  
|变量类型|说明|  
|----------|--------|  
|[简单变量](../c-language/simple-variable-declarations.md)|带整型或浮点型的单值变量|  
|[数组](../c-language/array-declarations.md)|由类型相同的一系列元素构成的变量|  
|[指针](../c-language/pointer-declarations.md)|指向其他变量并包含变量位置（以地址的形式）而不是值的变量|  
|[枚举变量](../c-language/c-enumeration-declarations.md)|带整型的简单变量，其中包含命名整数常量组中的某个值|  
|[结构](../c-language/structure-declarations.md)|由一系列可具有不同类型的值构成的变量|  
|[Unions](../c-language/union-declarations.md)|由占用相同的存储空间的不同类型的多个值构成的变量|  
  
 声明符是声明的一部分，它指定要引入程序中的名称。  它可以包括修饰符（如 **\*** \(pointer\-to\)）和任何 Microsoft 调用约定关键字。  
  
 **Microsoft 专用**  
  
 在声明符中  
  
```  
__declspec(thread) char *var;  
```  
  
 `char` 是类型说明符，`__declspec(thread)` 和 `*` 是修饰符，`var` 是标识符的名称。  
  
 **结束 Microsoft 专用**  
  
 可使用声明符声明值的数组、指向值的指针和返回指定类型的值的函数。  声明符出现在本节后面描述的数组和指针声明中。  
  
## 语法  
 `declarator`:  
 *pointer*  opt *direct\-declarator*  
  
 *direct\-declarator*:  
 *identifier*  
  
 **\(**  *declarator*  **\)**  
  
 *direct\-declarator*  **\[**  *constant\-expression*  opt **\]**  
  
 *direct\-declarator*  **\(**  *parameter\-type\-list*  **\)**  
  
 *direct\-declarator*  **\(**  *identifier\-list*  opt **\)**  
  
 `pointer`:  
 **\*** *type\-qualifier\-list*  opt  
  
 **\*** *type\-qualifier\-list*  opt `pointer`  
  
 *type\-qualifier\-list*:  
 *type\-qualifier*  
  
 *type\-qualifier\-list type\-qualifier*  
  
> [!NOTE]
>  有关引用 `declarator` 的语法，请参阅[声明概述](../c-language/overview-of-declarations.md)或 [C 语言语法摘要](../c-language/c-language-syntax-summary.md)中的 `declaration` 的语法。  
  
 当声明符包含未修改的标识符时，正在声明的项将具有基类型。  如果星号 \(**\***\) 显示在标识符的左侧，则将类型修改为指针类型。  如果标识符后跟方括号 \(**\[ \]**\)，则将类型修改为数组类型。  如果标识符后跟圆括号，则将类型修改为函数类型。  有关解释声明中的优先级的详细信息，请参阅[解释更复杂的声明符](../c-language/interpreting-more-complex-declarators.md)。  
  
 每个声明符至少声明一个标识符。  声明符必须包含一个类型说明符才能成为完整声明。  类型说明符提供了数组类型的元素的类型、由指针类型寻址的对象的类型或函数的返回类型。  
  
 [数组](../c-language/array-declarations.md)和[指针](../c-language/pointer-declarations.md)声明将在本节后面做更详细地讨论。  以下示例阐释声明符的几种简单形式：  
  
```  
int list[20]; // Declares an array of 20 int values named list  
char *cp;     // Declares a pointer to a char value  
double func( void ); // Declares a function named func, with no   
                     // arguments, that returns a double value  
int *aptr[10] // Declares an array of 10 pointers  
```  
  
 **Microsoft 专用**  
  
 Microsoft C 编译器不限制可修改算法、结构和联合类型的声明符的数目。  该数字仅受可用内存限制。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [声明和类型](../c-language/declarations-and-types.md)