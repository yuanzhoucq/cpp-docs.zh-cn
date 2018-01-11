---
title: "后缀增量和减量运算符: + + 和-|Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs: C++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e1d6c13da3023073f3d8b3e9625fa141253ba2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>后缀增量和减量运算符：++ 和 --
## <a name="syntax"></a>语法  
  
```  
postfix-expression ++  
postfix-expression --  
```  
  
## <a name="remarks"></a>备注  
 C++ 提供了前缀和后缀递增和递减运算符；本节仅介绍后缀递增和递减运算符。 (有关详细信息，请参阅[前缀递增和递减运算符](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)。)两者之间的区别是，在后缀表示法中，运算符出现在*后缀表达式*，而在前缀表示法中，运算符出现在之前*表达式。* 以下示例显示了一个后缀递增运算符：  
  
```  
i++;  
```  
  
 应用后缀递增运算符 (`++`) 的效果是操作数的值增加一个适当类型的单位。 同样，应用后缀递减运算符的效果 (**--**) 是操作数的值减少一个适当类型的单位。  
  
 务必要注意是，后缀递增或递减表达式计算结果为表达式的值**之前**各自的运算符的应用程序。 递增或递减运算发生**后**计算的操作数。 仅当在较大的表达式的上下文中发生后缀递增或递减运算时才会出现此问题。  
  
 当后缀运算符应用于函数参数时，在参数的值传递给函数之前，不能保证该值是递增还是递减。  有关详细信息，请参阅 C++ 标准中的 1.9.17 节。  
  
 将后缀递增运算符应用于指向类型的对象的数组的指针**长**实际上会将添加四个指针的内部表示。 此行为会导致指针，这以前称为 *n* th 元素的数组，来指代 (*n*+ 1) 个元素。  
  
 后缀递增运算符和后缀递减运算符的操作数必须是可修改 (不**const**) 的算法或指针类型的左值。 结果的类型是相同的*后缀表达式*，但它不再是左值。  
  
**Visual Studio 2017 15.3 及更高版本**(适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 操作数的后缀递增或递减运算符不能为类型`bool`。
  
 以下代码演示了后缀递增运算符：  
  
```  
// expre_Postfix_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 10;  
   cout << i++ << endl;  
   cout << i << endl;  
}  
```  
  
 不支持对枚举类型执行后递增和后递减操作：  
  
```  
enum Compass { North, South, East, West );  
Compass myCompass;  
for( myCompass = North; myCompass != West; myCompass++ ) // Error  
```  
  
## <a name="see-also"></a>请参阅  
 [后缀表达式](../cpp/postfix-expressions.md)   
 [C + + 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 后缀增量和减量运算符](../c-language/c-postfix-increment-and-decrement-operators.md)