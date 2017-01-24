---
title: "const_cast 运算符 | Microsoft Docs"
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
  - "const_cast"
  - "const_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_cast 关键字 [C++]"
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# const_cast 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从类中移除 **const**、`volatile` 和 **\_\_unaligned** 特性。  
  
## 语法  
  
```  
  
const_cast <   
type-id  
 > (   
expression  
 )  
  
```  
  
## 备注  
 指向任何对象类型的指针或指向数据成员的指针可显式转换为完全相同的类型（**const**、`volatile` 和 **\_\_unaligned** 限定符除外）。  对于指针和引用，结果将引用原始对象。  对于指向数据成员的指针，结果将引用与指向数据成员的原始（未强制转换）的指针相同的成员。  根据引用对象的类型，通过生成的指针、引用或指向数据成员的指针的写入操作可能产生未定义的行为。  
  
 您不能使用 `const_cast` 运算符直接重写常量变量的常量状态。  
  
 `const_cast` 运算符将 null 指针值转换为目标类型的 null 指针值。  
  
## 示例  
  
```  
// expre_const_cast_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class CCTest {  
public:  
   void setNumber( int );  
   void printNumber() const;  
private:  
   int number;  
};  
  
void CCTest::setNumber( int num ) { number = num; }  
  
void CCTest::printNumber() const {  
   cout << "\nBefore: " << number;  
   const_cast< CCTest * >( this )->number--;  
   cout << "\nAfter: " << number;  
}  
  
int main() {  
   CCTest X;  
   X.setNumber( 8 );  
   X.printNumber();  
}  
```  
  
 在包含 `const_cast` 的行中，`this` 指针的数据类型为 `const CCTest *`。  `const_cast` 运算符会将 `this` 指针的数据类型更改为 `CCTest *`，以允许修改成员 `number`。  强制转换仅对其所在的语句中的其余部分持续。  
  
## 请参阅  
 [强制转换运算符](../cpp/casting-operators.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)