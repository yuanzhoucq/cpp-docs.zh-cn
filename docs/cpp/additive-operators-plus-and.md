---
title: "加法运算符: + 和-|Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '-'
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- subtraction operator, additive operators
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
- '- operator, additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
caps.latest.revision: 9
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
ms.openlocfilehash: a1017985934cbe871617b76f3e5959121b810602
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="additive-operators--and--"></a>加法运算符：+ 和 -
## <a name="syntax"></a>语法  
  
```  
expression + expression   
expression - expression  
```  
  
## <a name="remarks"></a>备注  
 相加运算符为：  
  
-   加法 (**+**)  
  
-   减法 (**-**)  
  
 这些二进制运算符具有从左至右的关联性。  
  
 相加运算符采用算术或指针类型的操作数。 添加的结果 (**+**) 运算符是操作数之和。 减法运算的结果 (**-**) 运算符是操作数之差。 如果一个操作数是指针或两个操作数都是指针，则它们必须是指向对象的指针，而不是指向函数的指针。 如果两个操作数都是指针，则结果没有意义，除非它们是指向同一数组中的对象的指针。  
  
 相加运算符采用的操作数*算术*，*整型*，和*标量*类型。 下表定义了这些操作数。  
  
### <a name="types-used-with-additive-operators"></a>用于相加运算符的类型  
  
|类型|含义|  
|----------|-------------|  
|*算术运算*|整型和浮点类型统称为“算术”类型。|  
|*整型*|所有大小（long、short）和枚举数的 char 和 int 类型为“整数”类型。|  
|*标量*|标量操作数是算术类型或指针类型的操作数。|  
  
 这些运算符的合法组合为：  
  
 *算术* + *算术*  
  
 *标量* + *整型*  
  
 *整型* + *标量*  
  
 *算术* - *算术*  
  
 *标量* - *标量*  
  
 请注意，加法和减法不是等效运算。  
  
 如果两个操作数都是算术类型，在涵盖的转换[标准转换](standard-conversions.md)适用于操作数，并且结果为已转换的类型。  
  
## <a name="example"></a>示例  
  
```  
// expre_Additive_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
#define SIZE 5  
using namespace std;  
int main() {  
   int i = 5, j = 10;  
   int n[SIZE] = { 0, 1, 2, 3, 4 };  
   cout  << "5 + 10 = " << i + j << endl  
         << "5 - 10 = " << i - j << endl;  
  
   // use pointer arithmetic on array  
  
   cout << "n[3] = " << *( n + 3 ) << endl;  
}  
```  
  
## <a name="pointer-addition"></a>指针加法  
 在加法运算中，如果其中一个操作数是指向对象数组的指针，则另一个操作数必须是整型。 结果为与原始指针类型相同的指针和指向另一个数组元素的指针。 以下代码片段阐述了此概念：  
  
```  
short IntArray[10]; // Objects of type short occupy 2 bytes  
short *pIntArray = IntArray;  
  
for( int i = 0; i < 10; ++i )  
{  
    *pIntArray = i;  
    cout << *pIntArray << "\n";  
    pIntArray = pIntArray + 1;  
}  
```  
  
 虽然将整数值 1 添加到 `pIntArray`，但这并不表示“将 1 添加到该地址”，而是指“调整指针使其指向数组中的下一个对象”，而该对象恰好是在 2 字节（或者 `sizeof( int )`）之外。  
  
> [!NOTE]
>  在 C++ 程序中很少找到 `pIntArray = pIntArray + 1` 形式的代码；若要实现递增，以下形式更可取：`pIntArray++` 或 `pIntArray += 1`。  
  
## <a name="pointer-subtraction"></a>指针减法  
 如果两个操作数都是指针，则减法运算的结果就是两个操作数之差（在数组元素中）。 减法表达式产生类型 ptrdiff_t（在标准包含文件 STDDEF.H 中定义）的带符号的整数结果。  
  
 其中一个操作数可以是整型，条件是该操作数是第二操作数。 减法的结果的类型与原始指针的类型相同。 减法的值是指向的指针 (*n* - *我*) 个数组元素，其中* n *是由指向元素原始指针和*我*是第二个操作数的整数值。  
  
## <a name="see-also"></a>另请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C + + 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 加法运算符](../c-language/c-additive-operators.md)
