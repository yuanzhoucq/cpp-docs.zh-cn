---
title: "Address-of 运算符：&amp; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "address-of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 运算符"
  - "& 运算符, address-of 运算符"
  - "address-of 运算符 (&)"
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Address-of 运算符：&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
& cast-expression  
```  
  
## 备注  
 一元 address\-of 运算符 \(**&**\) 采用其操作数的地址。  address\-of 运算符的操作数可以是函数指示符，也可以是指定不是位域且不使用 **register** 储存类说明符声明的对象的左值。  
  
 address\-of 运算符仅适用于具有基本、结构、类或在文件范围级别声明的联合类型的变量，或仅适用于下标数组引用。  在这些表达式中，可在 address\-of 表达式中添加或提取不包括 address\-of 运算符的常数表达式。  
  
 当应用于函数或左值时，该表达式的结果将是派生自操作数类型（右值）的指针类型。  例如，如果操作数的类型为 `char`，则表达式的结果为指向 `char` 的类型指针。  address\-of 运算符（应用于 **const** 或 `volatile` 对象）的计算结果为 **const** `type` **\*** 或 `volatile` `type` **\***，其中 `type` 是原始对象的类型。  
  
 在将 address\-of 运算符应用于[限定名](http://msdn.microsoft.com/zh-cn/3fefb16d-8120-4627-8b3f-3d90fbdcd1df)时，结果将取决于 *qualified\-name* 是否指定静态成员。  如果是这样，则结果为指向成员声明中指定的类型的指针。  如果该成员不是静态的，则结果为指向由 *qualified\-class\-name* 指示的类的成员 *name* 的指针。（有关 *qualified\-class\-name* 的详细信息，请参阅[主表达式](../cpp/primary-expressions.md)。）以下代码段说明了结果的不同之处，取决于该成员是否为静态的：  
  
```  
// expre_Address_Of_Operator.cpp  
// C2440 expected  
class PTM {  
public:  
           int   iValue;  
    static float fValue;  
};  
  
int main() {  
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static  
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static  
   float *spfValue     = &PTM::fValue;  // OK  
}  
```  
  
 在此示例中，由于 `fValue` 是静态成员，因此表达式 `&PTM::fValue` 产生类型 `float *` 而不是类型 `float PTM::*`。  
  
 仅当明确要引用的函数的版本时，才能采用重载函数的地址。  有关如何获取特定重载函数的地址的信息，请参阅[重载函数的地址](../misc/address-of-overloaded-functions.md)。  
  
 通过将 address\-of 运算符应用于引用类型，可获得与将该运算符应用于引用绑定到的对象所获得的结果相同的结果。  例如：  
  
## 示例  
  
```  
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
  
## Output  
  
```  
&d equals &rd  
```  
  
 以下示例使用 address\-of 运算符将指针参数传递给函数：  
  
```  
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
  
## Output  
  
```  
25  
```  
  
## 请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Lvalue 引用声明符：&](../cpp/lvalue-reference-declarator-amp.md)   
 [间接寻址和 Address\-of 运算符](../c-language/indirection-and-address-of-operators.md)