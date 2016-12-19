---
title: "数组声明 | Microsoft Docs"
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
  - "数组 [C++], 声明"
  - "声明数组"
  - "多维数组"
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数组声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“数组声明”将命名数组并指定其元素的类型。  它还可定义数组中的元素数。  带数组类型的变量被视为指向数组元素的类型的指针。  
  
## 语法  
 `declaration`:  
 *declaration\-specifiers init\-declarator\-list*  opt               **;**  
  
 *init\-declarator\-list*:  
 *init\-declarator*  
  
 *init\-declarator\-list* **,**  *init\-declarator*  
  
 *init\-declarator*:  
 *declarator*  
  
 *declarator*  **\=**  *initializer*  
  
 `declarator`:  
 *pointer*  opt *direct\-declarator*  
  
 *direct\-declarator*:  
 *direct\-declarator*  **\[**  *constant\-expression*  opt **\]**  
  
 由于 *constant\-expression* 是可选的，因此该语法有两种形式：  
  
-   第一种形式定义一个数组变量。  括号内的 *constant\-expression* 参数指定数组中的元素数。  *constant\-expression*（如果有）必须具有整型和大于零的值。  每个元素均具有 *type\-specifier* 给定的类型，可以是除 `void` 之外的任何类型。  数组元素不能是函数类型。  
  
-   第二种形式声明已在其他位置定义了变量。  它省略括号中的 *constant\-expression* 参数而不是括号。  仅在之前已初始化数组、将其声明为参数或声明为对在程序中的其他位置显式定义的某个数组的引用的情况下才能使用此形式。  
  
 在两种形式中，*direct\-declarator* 都会命名变量并且可以修改变量的类型。  紧跟 *direct\-declarator* 的方括号 \(**\[ \]**\) 会将声明符修改为数组类型。  
  
 类型限定符可以出现在数组类型对象的声明中，但限定符应用于元素而不是数组本身。  
  
 您可以声明一系列数组（“多维”数组），方法是遵循以下形式的带括号的常量表达式的列表的数组声明符：  
  
```  
  
type-specifier declarator [constant-expression] [constant-expression] ...  
```  
  
 方括号中的每个 *constant\-expression* 均定义给定维度中的元素数：二维数组具有两个带括号的表达式，三维数组具有三个带括号的表达式，依此类推。  如果您已初始化数组、将其声明为参数或声明为对在程序中的其他位置显式定义的某个数组的引用，则可以忽略第一个常量表达式。  
  
 可使用复杂的声明符定义指向各种类型的对象的指针的数组，如[解释更复杂的声明符](../c-language/interpreting-more-complex-declarators.md)中所述。  
  
 按行存储数组。  例如，下面的数组包含两个行，每个行具有三个列：  
  
```  
char A[2][3];  
```  
  
 首先存储第一行的三个列，然后存储第二行的三个列。  这意味着最后一个下标的变化速度最快。  
  
 若要引用数组的单个元素，请使用下标表达式，如[后缀运算符](../c-language/postfix-operators.md)中所述。  
  
## 示例  
 这些示例阐释了数组声明：  
  
```  
float matrix[10][15];  
```  
  
 名为 `matrix` 的二维数组具有 150 个元素，其中每个元素具有 **float** 类型。  
  
```  
struct {  
    float x, y;  
} complex[100];  
```  
  
 这是结构数组的声明。  此数组有 100 个元素；每个元素均为一个包含两个成员的结构。  
  
```  
extern char *name[];  
```  
  
 此语句声明指向 `char` 的指针数组的类型和名称。  `name` 的实际定义会在其他位置出现。  
  
 **Microsoft 专用**  
  
 保存数组的最大大小所需的整数类型为 **size\_t** 的大小。  头文件 STDDEF.H 中定义的 **size\_t** 是一个 `unsigned int`，其范围从 0x00000000 到 0x7CFFFFFF。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [声明符和变量声明](../c-language/declarators-and-variable-declarations.md)