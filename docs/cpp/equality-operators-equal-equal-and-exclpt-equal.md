---
title: '相等运算符: = = 和 ！ = |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- not_eq
- '!='
- ==
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2be0d4cf45bbedc5e799b07962c05f845d5f3efe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="equality-operators--and-"></a>相等运算符：== 和 !=
## <a name="syntax"></a>语法  
  
```  
expression == expression  
expression != expression  
```  
  
## <a name="remarks"></a>备注  
 二元相等运算符将严格比较其操作数的相等性或不相等性。  
  
 相等运算符（等于 (`==`) 而不等于 (`!=`)）的优先级低于关系运算符的优先级，但其行为类似。 这些运算符的结果类型为 `bool`。  
  
 相等运算符 (`==`) 返回**true** (1) 如果两个操作数具有相同的值; 否则，它将返回**false** (0)。 不等于运算符 (`!=`) 返回**true**如果操作数不具有相同的值; 否则，它将返回**false**。  
  
## <a name="operator-keyword-for-"></a>!= 的运算符关键字  
 `not_eq` 运算符是 `!=` 的文本等效项。 有两种方法来访问`not_eq`在程序中的运算符： 包含头文件`iso646.h`，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展） 编译器选项。  
  
## <a name="example"></a>示例  
  
```  
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 相等运算符可比较指向同一类型的成员的指针。 在这种比较中，则执行指针到成员转换。 指向成员的指针也可以与计算结果为 0 的常量表达式进行比较。  
  
## <a name="see-also"></a>请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C++ 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 关系和相等运算符](../c-language/c-relational-and-equality-operators.md)