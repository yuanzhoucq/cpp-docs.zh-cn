---
title: Address-of 运算符： &amp; |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8acd615cb2f05e62019f5076a423ae0f8218815a
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406001"
---
# <a name="address-of-operator-amp"></a>Address-of 运算符： &amp;
## <a name="syntax"></a>语法  
  
```  
& cast-expression  
```  
  
## <a name="remarks"></a>备注  
 一元 address-of 运算符 (**&**) 采用其操作数的地址。 Address-of 运算符的操作数可以是函数指示符或指定一个对象，它不是位域是左值。  
  
 address-of 运算符仅适用于具有基本、结构、类或在文件范围级别声明的联合类型的变量，或仅适用于下标数组引用。 在这些表达式中，可在 address-of 表达式中添加或提取不包括 address-of 运算符的常数表达式。  
  
 当应用于函数或左值时，该表达式的结果将是派生自操作数类型（右值）的指针类型。 例如，如果操作数的类型**char**，该表达式的结果是指针类型的**char**。 Address-of 运算符，应用于**const**或**易失性**对象，计算结果为`const type *`或`volatile type *`，其中**类型**是原始的类型对象。  
  
 当 address-of 运算符应用于限定名时，结果取决于是否*限定名称*指定静态成员。 如果是这样，则结果为指向成员声明中指定的类型的指针。 如果该成员不是静态的结果是指向成员的指针*名称*指示的类的*限定类名*。 (请参阅[主表达式](../cpp/primary-expressions.md)有关详细信息*限定类名*。)以下代码段说明了结果的不同之处，取决于该成员是否为静态的：  
  
```cpp 
// expre_Address_Of_Operator.cpp  
// C2440 expected  
class PTM {  
public:  
    int iValue;  
    static float fValue;  
};  
  
int main() {  
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static  
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static  
   float *spfValue     = &PTM::fValue;  // OK  
}  
```  
  
 在此示例中，由于 `&PTM::fValue` 是静态成员，因此表达式 `float *` 产生类型 `float PTM::*` 而不是类型 `fValue`。  
  
 仅当明确要引用的函数的版本时，才能采用重载函数的地址。 请参阅[函数重载](function-overloading.md)有关如何获取特定的地址信息的重载函数。  
  
 通过将 address-of 运算符应用于引用类型，可获得与将该运算符应用于引用绑定到的对象所获得的结果相同的结果。 例如：  
  
## <a name="example"></a>示例  
  
```cpp 
// expre_Address_Of_Operator2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   double d;        // Define an object of type double.  
   double& rd = d;  // Define a reference to the object.  
  
   // Obtain and compare their addresses  
   if( &d == &rd )  
      cout << "&d equals &rd" << endl;  
}  
```  
  
## <a name="output"></a>输出  
  
```Output  
&d equals &rd  
```  
  
 以下示例使用 address-of 运算符将指针参数传递给函数：  
  
```cpp 
// expre_Address_Of_Operator3.cpp  
// compile with: /EHsc  
// Demonstrate address-of operator &  
  
#include <iostream>  
using namespace std;  
  
// Function argument is pointer to type int  
int square( int *n ) {  
   return (*n) * (*n);  
}  
  
int main() {  
   int mynum = 5;  
   cout << square( &mynum ) << endl;   // pass address of int  
}  
```  
  
## <a name="output"></a>输出  
  
```Output  
25  
```  
  
## <a name="see-also"></a>请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C++ 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [左值引用声明符： &](../cpp/lvalue-reference-declarator-amp.md)   
 [间接寻址运算符和 Address-of 运算符](../c-language/indirection-and-address-of-operators.md)