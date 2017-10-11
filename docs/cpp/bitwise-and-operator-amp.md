---
title: "按位与运算符： &amp; |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bitand
dev_langs:
- C++
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 99ff65f38abf5cfcac135e2cc54e3df6df5f336d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="bitwise-and-operator-amp"></a>按位与运算符：&amp;
## <a name="syntax"></a>语法  
  
```  
  
expression   
&  
 expression  
  
```  
  
## <a name="remarks"></a>备注  
 表达式可以是其他“与”表达式，或（遵循下面所述的类型限制）相等表达式、关系表达式、加法表达式、乘法表达式、指向成员的指针表达式、强制转换表达式、一元表达式、后缀表达式或主表达式。  
  
 按位 AND 运算符 (**&**) 的每个位与第二个操作数的相应位的第一个操作数将进行比较。 如果两个位均为 1，则对应的结果位将设置为 1。 否则，将对应的结果位设置为 0。  
  
 按位“与”运算符的两个操作数必须为整型。 中涵盖的常用算术转换[标准转换](standard-conversions.md)，适用于操作数。  
  
## <a name="operator-keyword-for-"></a>运算符关键字 （& a)  
 `bitand`运算符是文本等效项** & **。 有两种方法来访问`bitand`在程序中的运算符： 包含头文件`iso646.h`，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展） 编译器选项。  
  
## <a name="example"></a>示例  
  
```  
// expre_Bitwise_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise AND  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0xFFFF;      // pattern 1111 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [C++ 内置运算符、优先级和关联性](cpp-built-in-operators-precedence-and-associativity.md)  
 [C + + 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 按位运算符](../c-language/c-bitwise-operators.md)
