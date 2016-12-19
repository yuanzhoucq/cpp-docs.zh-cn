---
title: "参数 | Microsoft Docs"
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
  - "参数 [C++], 函数"
  - "函数参数"
  - "函数调用, 参数"
  - "函数参数"
  - "函数参数, 关于函数参数"
  - "函数 [C], 参数"
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 参数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

函数调用中的参数具有此形式：  
  
```  
  
expression ( expression-list <SUB>opt</SUB> )  /* Function call */  
```  
  
 在函数调用中，*expression\-list* 是表达式的列表（用逗号分隔）。  后面这些表达式的值是传递给函数的参数。  如果函数不采用参数，则 *expression\-list* 应包含关键字 `void`。  
  
 参数可以是具有基本、结构、联合或指针类型的任何值。  通过值传递所有参数。  这意味着，参数的副本将分配给对应的参数。  该函数不了解已传递的参数的实际内存位置。  该函数使用此副本，而不影响其最初派生自的变量。  
  
 虽然您无法将数组或函数作为参数传递，但可以将指针传递给这些项。  利用指针，函数可以通过引用访问值。  由于指向变量的指针包含该变量的地址，因此该函数可以使用此地址访问该变量的值。  指针参数允许函数访问数组和函数，即使数组和函数不能作为参数传递。  
  
 计算参数的顺序因不同的编译器和不同的优化级别而异。  但是，在输入函数之前，将完全计算参数和任何副作用。  有关副作用的信息，请参阅[副作用](../c-language/side-effects.md)。  
  
 计算函数调用中的 *expression\-list*，并在函数调用中对每个参数执行常用算术转换。  如果原型可用，则生成的参数类型将与原型的对应参数进行比较。  如果这些参数不匹配，则执行转换或发布诊断消息。  参数还执行常用算术转换。  
  
 除非函数的原型或定义显式指定参数的变量数目，否则 *expression\-list* 中的表达式的数目必须与参数的数目匹配。  在这种情况下，编译器将检查与参数列表中的类型名称一样多的参数，并根据需要转换这些参数，如上所述。  有关详细信息，请参阅[使用参数的变量数目进行调用](../c-language/calls-with-a-variable-number-of-arguments.md)。  
  
 如果原型的参数列表只包含关键字 `void`，则编译器需要在函数调用和定义中使用零参数。  如果编译器找到任何参数，则会发出该诊断消息。  
  
## 示例  
 此示例将指针用作参数：  
  
```  
int main()  
{  
    /* Function prototype */  
  
    void swap( int *num1, int *num2 );  
    int x, y;  
    .  
    .  
    .  
    swap( &x, &y );  /* Function call */  
}  
  
/* Function definition */  
  
void swap( int *num1, int *num2 )  
{  
    int t;  
  
    t = *num1;  
    *num1 = *num2;  
    *num2 = t;  
}  
```  
  
 在此示例中，`swap` 函数在 `main` 中声明且具有两个参数，分别用标识符 `num1` 和 `num2` 表示，二者都是指向 `int` 值的指针。  此外，还将原型样式定义中的参数 `num1` 和 `num2` 声明为指向 `int` 类型值的指针。  
  
 在函数调用中  
  
```  
swap( &x, &y )  
```  
  
 `x` 的地址存储在 `num1` 中，而 `y` 的地址存储在 `num2` 中。  现在，这两个名称或“别名”存在于同一个位置。  对 `swap` 中的 `*num1` 和 `*num2` 的引用是对 `main` 中的 `x` 和 `y` 的有效引用。  `swap` 中的赋值实际交换了 `x` 和 `y` 的内容。  因此，`return` 语句不是必需的。  
  
 编译器对 `swap` 的参数执行类型检查，因为 `swap` 的原型包含每个参数的参数类型。  原型和定义的括号内的标识符可能相同，也可能不同。  重要的一点是，参数的类型与原型和定义中的这些参数列表相匹配。  
  
## 请参阅  
 [函数调用](../c-language/function-calls.md)