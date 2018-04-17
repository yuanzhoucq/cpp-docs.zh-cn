---
title: "关系运算符： &lt;， &gt;， &lt;=、 和&gt;= |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- <
- '>'
dev_langs:
- C++
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28d7cf77f9bea05a9220aea3d4006f64899b84ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>关系运算符： &lt;， &gt;， &lt;=、 和&gt;=
## <a name="syntax"></a>语法  
  
```  
expression < expression  
expression > expression  
expression <= expression  
expression >= expression  
```  
  
## <a name="remarks"></a>备注  
 二进制关系运算符确定下列关系：  
  
-   小于 (**\<**)  
  
-   大于 (**>**)  
  
-   小于或等于 (**\<=**)  
  
-   大于或等于 (**>=**)  
  
 关系运算符具有从左到右的关联性。 关系运算符的两个操作数必须是算术或指针类型。 它们将生成 `bool` 类型的值。 返回的值为**false** (0) 如果在表达式中的关系为 false; 否则为返回的值是**true** (1)。  
  
## <a name="example"></a>示例  
  
```  
// expre_Relational_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << "The true expression 3 > 2 yields: "  
         << (3 > 2) << endl  
         << "The false expression 20 < 10 yields: "  
         << (20 < 10) << endl;  
}  
```  
  
 前面的示例中的表达式必须括在括号中，因为流插入运算符 (**<<**) 优先级高于关系运算符。 因此，未括在括号中的第一个表达式的计算结果将为：  
  
```  
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 中涵盖的常用算术转换[标准转换](standard-conversions.md)应用于算术类型的操作数。  
  
## <a name="comparing-pointers"></a>比较指针  
 在比较两个指向同一类型的对象的指针时，结果由程序的地址空间中所指向的对象的位置决定。 也可以将指针与计算结果为 0 的常量表达式或 void * 类型的指针进行比较。 如果指针执行指针比较类型的指针针对 void \*，另一个指针将隐式转换为类型 void \*。 然后进行比较。  
  
 不能比较两个类型不同的指针，除非：  
  
-   一个类型是派生自另一个类型的类类型。  
  
-   至少有一个指针显式转换（强制转换）为类型 void *。 (另一个指针将隐式转换为类型 void\*进行转换。)  
  
 两个指向同一对象的相同类型的指针一定是相等的。 如果比较两个指向对象的非静态成员的指针，则以下规则将适用：  
  
-   如果类类型不是联合，并且两个成员不隔开*访问说明符*，例如，公共、 受保护或私有的指向声明的成员的指针上次将大于指向声明的成员的指针更早版本。  
  
-   如果两个成员被隔离*访问说明符*，结果不确定。  
  
-   如果类类型是联合，则指向该联合中不同的数据成员的指针是相等的。  
  
 如果两个指针指向同一数组的元素或指向超出数组末尾 1 的元素，则指向带较高下标的对象的指针会更高。 仅当指针引用同一数组中的对象或超出数组末尾 1 的位置时，才能保证指针比较有效。  
  
## <a name="see-also"></a>请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C++ 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 关系和相等运算符](../c-language/c-relational-and-equality-operators.md)