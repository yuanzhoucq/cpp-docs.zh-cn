---
title: "乘法运算符和取模运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '%'
- /
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator, C+
- '* operator'
- division operator, multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
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
ms.openlocfilehash: b63a36817bb0366d21fba11c5e1e4eccbcc6951f
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>乘法运算符和取模运算符
## <a name="syntax"></a>语法  
  
```  
expression * expression   
expression / expression   
expression % expression  
```  
  
## <a name="remarks"></a>备注  
 乘法运算符为：  
  
-   乘法 (**\***)  
  
-   除法 (**/**)  
  
-   取模（除法运算的余数）(`%`)  
  
 这些二进制运算符具有从左至右的关联性。  
  
 乘法运算符采用算术类型的操作数。 取模运算符 (`%`) 具有更严格的要求，即其操作数必须是整型。 (若要获取浮点除法运算的余数，请使用运行时函数： [fmod](../c-runtime-library/reference/fmod-fmodf.md)。)中涵盖的转换[标准转换](standard-conversions.md)适用于操作数，并且结果为已转换的类型。  
  
 除法运算符产生的结果为将第一个操作数乘以第二个操作数所获得的结果。  
  
 除法运算符产生的结果为将第一个操作数除以第二个操作数所获得的结果。  
  
 取模运算符产生下列表达式中，给定的余数其中*e1*是第一个操作数和*e2*是第二个： *e1* -(*e1* /  *e2*) \* *e2*，其中两个操作数都是整型。  
  
 在除法或取模表达式中被 0 除的结果是不确定的，将会导致运行时错误。 因此，以下表达式生成未定义的错误结果：  
  
```  
i % 0  
f / 0.0  
```  
  
 如果乘法、除法或取模表达式的两个操作数具有相同的符号，则结果为正。 否则，结果为负。 取模运算的符号的结果是实现定义的。  
  
> [!NOTE]
>  由于在溢出或下溢条件不提供由乘法运算符执行的转换，因此，如果乘法操作的结果在转换后不能用操作数类型表示，则信息可能丢失。  
  
## <a name="microsoft-specific"></a>Microsoft 专用  
 在 Microsoft C++ 中，取模表达式的结果的符号始终与第一个操作数的符号相同。  
  
**结束 Microsoft 专用**  
 如果两个整数的减法计算不准确，并且只有一个操作数为负，则结果是最大的整数（在数量级上，忽略符号），该整数小于减法运算所生成的准确值。 例如，计算的值-11 / 3 是-3.666666666。 该整数除法的结果是-3。  
  
 乘法运算符之间的关系由标识 (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*。  
  
## <a name="example"></a>示例  
 以下程序演示乘法运算符。 请注意，其中一个操作数的`10 / 3`必须显式转换为类型`float`以避免截断，以便两个操作数的类型`float`在除法运算前。  
  
```  
// expre_Multiplicative_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   int x = 3, y = 6, z = 10;  
   cout  << "3 * 6 is " << x * y << endl  
         << "6 / 3 is " << y / x << endl  
         << "10 % 3 is " << z % x << endl  
         << "10 / 3 is " << (float) z / x << endl;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C + + 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 乘法运算符](../c-language/c-multiplicative-operators.md)
