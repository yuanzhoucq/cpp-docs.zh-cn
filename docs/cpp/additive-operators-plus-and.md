---
title: '加法运算符: + 和-|Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89fc0f122f0859e6fc891ddfccd4bc99e7034bfe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943026"
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
  
 相加运算符采用算术或指针类型的操作数。 相加的结果 (**+**) 运算符是操作数之和。 该减法运算的结果 (**-**) 运算符是操作数之差。 如果一个操作数是指针或两个操作数都是指针，则它们必须是指向对象的指针，而不是指向函数的指针。 如果两个操作数都是指针，则结果没有意义，除非它们是指向同一数组中的对象的指针。  
  
 相加运算符采用的操作数*算术*，*整型*，并*标量*类型。 下表定义了这些操作数。  
  
### <a name="types-used-with-additive-operators"></a>用于相加运算符的类型  
  
|类型|含义|  
|----------|-------------|  
|*算术运算*|整型和浮点类型统称为“算术”类型。|  
|*integral*|所有大小（long、short）和枚举数的 char 和 int 类型为“整数”类型。|  
|*scalar*|标量操作数是算术类型或指针类型的操作数。|  
  
 这些运算符的合法组合为：  
  
 *算术* + *算术*  
  
 *scalar* + *integral*  
  
 *integral* + *scalar*  
  
 *算术* - *算术*  
  
 *scalar* - *scalar*  
  
 请注意，加法和减法不是等效运算。  
  
 如果两个操作数都是算术类型，在涵盖的转换[标准转换](standard-conversions.md)适用于操作数，结果为转换的类型。  
  
## <a name="example"></a>示例  
  
```cpp 
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
  
```cpp 
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
 如果两个操作数都是指针，则减法运算的结果就是两个操作数之差（在数组元素中）。 减法表达式产生类型的有符号整数结果**ptrdiff_t** (在标准包含文件中定义\<stddef.h >)。  
  
 其中一个操作数可以是整型，条件是该操作数是第二操作数。 减法的结果的类型与原始指针的类型相同。 该减法运算的值是指向的 (*n* - *我*) 个数组元素，其中*n*指向的元素通过原始指针并*我*是第二个操作数的整数值。  
  
## <a name="see-also"></a>请参阅  
 [使用二进制运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C++ 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 加法运算符](../c-language/c-additive-operators.md)
