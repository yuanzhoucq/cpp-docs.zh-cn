---
title: "按位异或运算符: ^ |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
caps.latest.revision: 7
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
ms.openlocfilehash: c6d7713a28fa6c0dbe7a5543afa65cd927f614e7
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="bitwise-exclusive-or-operator-"></a>按位异或运算符：^
## <a name="syntax"></a>语法  
  
```  
expression ^ expression  
```  
  
## <a name="remarks"></a>备注  
按位异或运算符 (**^**) 将每个位与第一个操作数与其第二操作数的相应位进行比较。 如果一个位是 0，另一个位是 1，则相应的结果位将设置为 1。 否则，将对应的结果位设置为 0。  
  
按位“异或”运算符的两个操作数都必须为整型。 中涵盖的常用算术转换[标准转换](standard-conversions.md)适用于操作数。  
  
## <a name="operator-keyword-for-"></a>^ 的运算符关键字  
**Xor**运算符是文本等效项** ^ **。 有两种方法来访问**xor**在程序中的运算符： 包含头文件`iso646.h`，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展） 编译器选项。  
  
## <a name="example"></a>示例  
  
```cpp  
// expre_Bitwise_Exclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise exclusive OR  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xFFFF;      // pattern 1111 ...  
  
   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   



