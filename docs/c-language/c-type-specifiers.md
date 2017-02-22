---
title: "C 类型说明符 | Microsoft Docs"
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
  - "说明符, 类型"
  - "类型说明符, C"
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# C 类型说明符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明中的类型说明符定义变量或函数声明的类型。  
  
## 语法  
 *type\-specifier*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct\-or\-union\-specifier*  
  
 *enum\-specifier*  
  
 *typedef\-name*  
  
 **signed char**、**signed int**、**signed short int** 和 **signed long int** 类型与其 `unsigned` 对等项和 `enum` 一起称作“整型”。  **float**、**double** 和 `long double` 类型说明符称作“浮动”或“浮点”类型。  可在变量或函数声明中使用任何整型或浮点型说明符。  如果声明中未提供 *type\-specifier*，则将它用作 `int`。  
  
 可选关键字 **signed** 和 `unsigned` 可位于任何整型的前面或后面（`enum` 除外），也可将其单独用作类型说明符（在这种情况下，它们分别被理解为 **signed int** 和 `unsigned int`）。  单独使用时，关键字 `int` 被假定为 **signed**。  单独使用时，关键字 **long** 和 **short** 被理解为 **long int** 和 `short int`。  
  
 枚举类型被视为基本类型。  [枚举声明](../c-language/c-enumeration-declarations.md)中讨论了枚举类型的类型说明符。  
  
 关键字 `void` 有三种用途：指定函数返回类型、为未采用参数的函数指定一个参数类型列表以及指定一个指向未指定的类型的指针。  可以使用 `void` 类型声明不返回值的函数或声明指向未指定的类型的指针。  有关 `void` 单独出现在括号中且跟在函数名称后时的相关信息，请参阅[参数](../c-language/arguments.md)。  
  
 **Microsoft 专用**  
  
 类型检查现在是 ANSI 兼容的，这意味着 **short** 类型和 `int` 类型是不同类型。  例如，下面是编译器的早期版本接受的 Microsoft C 编译器中的一个重新定义。  
  
```  
int   myfunc();  
short myfunc();  
```  
  
 下一个示例还会生成有关到不同类型的间接寻址的警告：  
  
```  
int *pi;  
short *ps;  
  
ps = pi;  /* Now generates warning */  
```  
  
 Microsoft C 编译器还生成保留符号的差异警告。  例如：  
  
```  
signed int *pi;  
unsigned int *pu  
  
pi = pu;  /* Now generates warning */  
```  
  
 为副作用计算类型 `void` 表达式。  无论如何，不能使用具有 `void` 类型的表达式的值（不存在），也不能将 `void` 表达式转换为除 `void` 以外的任何类型（通过隐式或显式转换）。  如果您在需要 `void` 表达式的上下文中确实使用了任何其他类型的表达式，则其值将被丢弃。  
  
 为了符合 ANSI 规范，**void\*\*** 不能用作 **int\*\***。  仅 **void\*** 可用作指向未指定的类型的指针。  
  
 **结束 Microsoft 专用**  
  
 可以使用 `typedef` 声明创建附加类型说明符，如 [Typedef 声明](../c-language/typedef-declarations.md)中所述。  有关每个类型的大小的信息，请参阅[基本类型的存储](../c-language/storage-of-basic-types.md)。  
  
## 请参阅  
 [声明和类型](../c-language/declarations-and-types.md)