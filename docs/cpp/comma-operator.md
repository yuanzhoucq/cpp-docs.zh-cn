---
title: 逗号运算符:，|Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '%2C'
dev_langs:
- C++
helpviewer_keywords:
- comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a139efed1fadd8f7b821363b7cb9cdbf97c9a29
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409182"
---
# <a name="comma-operator-"></a>逗号运算符：,
允许对两个语句进行分组，其中有一个是预期的。  
  
## <a name="syntax"></a>语法  
  
```  
expression , expression  
```  
  
## <a name="remarks"></a>备注  
 逗号运算符具有从左向右的关联性。 由逗号分隔的两个表达式将从左向右进行计算。 始终计算左操作数，并且在计算右操作数之前将完成所有副作用。  
  
 在某些上下文（如函数参数列表）中，逗号可用作分隔符。 不要将该逗号用作分隔符与将其用作运算符的情况混淆；这两种用法完全不同。  
  
 考虑表达式  
  
 *e1* ， *e2*  
  
 类型和表达式的值是类型和值*e2*; 的计算结果*e1*将被丢弃。 如果右操作数是左值，则结果为左值。  
  
 在通常将逗号用作分隔符的方案中（例如，在函数或聚合初始值设定项的实参中），逗号运算符及其操作数必须包含在括号中。 例如：  
  
```cpp 
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 在上面的对 `func_one` 的函数调用中，会传递以逗号分隔的三个参数：`x`、`y + 2` 和 `z`。 在对 `func_two` 的函数调用中，圆括号强制编译器将第一个逗号解释为顺序计算运算符。 此函数调用将两个参数传递给 `func_two`。 第一个参数是顺序计算运算 `(x--, y + 2)` 的结果，具有表达式 `y + 2` 的值和类型；第二个参数为 `z`。  
  
## <a name="example"></a>示例  
  
```cpp 
// cpp_comma_operator.cpp  
#include <stdio.h>  
int main () {  
   int i = 10, b = 20, c= 30;  
   i = b, c;  
   printf("%i\n", i);  
  
   i = (b, c);  
   printf("%i\n", i);  
}  
```  
  
```Output  
20  
30  
```  
  
## <a name="see-also"></a>请参阅  
 [使用二进制运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C++ 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [顺序评估运算符](../c-language/sequential-evaluation-operator.md)