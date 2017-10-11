---
title: "const_cast 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- const_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 8f72367cb4970b2ce0121efc43b79691155808df
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="constcast-operator"></a>const_cast 运算符
删除**const**， `volatile`，和**__unaligned**从类的属性。  
  
## <a name="syntax"></a>语法  
  
```  
  
const_cast <   
type-id  
 > (   
expression  
 )  
  
```  
  
## <a name="remarks"></a>备注  
 指向任何对象类型的指针或指向数据成员的指针可以显式转换为的类型属于相同除**const**， `volatile`，和**__unaligned**限定符。 对于指针和引用，结果将引用原始对象。 对于指向数据成员的指针，结果将引用与指向数据成员的原始（未强制转换）的指针相同的成员。 根据引用对象的类型，通过生成的指针、引用或指向数据成员的指针的写入操作可能产生未定义的行为。  
  
 您不能使用 `const_cast` 运算符直接重写常量变量的常量状态。  
  
 `const_cast` 运算符将 null 指针值转换为目标类型的 null 指针值。  
  
## <a name="example"></a>示例  
  
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
  
 在包含 `const_cast` 的行中，`this` 指针的数据类型为 `const CCTest *`。 `const_cast` 运算符会将 `this` 指针的数据类型更改为 `CCTest *`，以允许修改成员 `number`。 强制转换仅对其所在的语句中的其余部分持续。  
  
## <a name="see-also"></a>另请参阅  
 [强制转换运算符](../cpp/casting-operators.md)   
 [关键字](../cpp/keywords-cpp.md)
