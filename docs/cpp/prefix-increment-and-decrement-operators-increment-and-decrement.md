---
title: '前缀增量和减量运算符: + + 和-|Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 071f21080bd093e5cb299471c8de7009741482f6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>前缀增量和减量运算符：++ 和 --
## <a name="syntax"></a>语法  
  
```  
++ unary-expression  
-- unary-expression  
```  
  
## <a name="remarks"></a>备注  
 前缀递增运算符 (`++`) 向其操作数添加 1；此递增值是表达式的结果。 操作数必须是左值不是类型**const**。 结果是与操作数相同类型的左值。  
  
 前缀递减运算符 (**--**) 是前缀递增运算符类似，只不过操作数将减少 1，并且结果是递减值。  

 **Visual Studio 2017 15.3 及更高版本**(适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md)): 递增或递减运算符的操作数可以不是类型`bool`。
  
 前缀和后缀递增和递减运算符均会影响其操作数。 它们之间的主要差异是递增或递减在表达式的计算中出现的顺序。 (有关详细信息，请参阅[后缀递增和递减运算符](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)。)在前缀形式中，将在表达式计算中使用值之前进行递增或递减，因此表达式的值与操作数的值不同。 在后缀形式中，将在表达式计算中使用值之后进行递增或递减，因此表达式的值与操作数的值相同。 例如，以下程序将打印“`++i = 6`”：  
  
```  
// expre_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int i = 5;  
   cout << "++i = " << ++i << endl;  
}  
```  
  
 整型或浮动类型的操作数将按整数值 1 递增或递减。 结果的类型与操作数类型相同。 指针类型的操作数将按其所寻址对象的大小递增或递减。 递增的指针将指向下一个对象；递减的指针将指向上一个对象。  
  
 由于递增和递减运算符具有副作用，使用递增或递减运算符在表达式[预处理器宏](../preprocessor/macros-c-cpp.md)可以导致意外结果。 请看以下示例：  
  
```  
// expre_Increment_and_Decrement_Operators2.cpp  
#define max(a,b) ((a)<(b))?(b):(a)  
  
int main()  
{  
   int i = 0, j = 0, k;  
   k = max( ++i, j );  
}  
```  
  
 宏将扩展为：  
  
```  
k = ((++i)<(j))?(j):(++i);  
```  
  
 如果 `i` 大于或等于 `j` 或者比 `j` 小 1，则将递增两次。  
  
> [!NOTE]
>  由于 C++ 内联函数会消除副作用（如此处描述的副作用），并允许语言执行更全面的类型检查，因此在很多情况下 C++ 内联函数较宏更为可取。  
  
## <a name="see-also"></a>请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C++ 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [前缀增量和减量运算符](../c-language/prefix-increment-and-decrement-operators.md)