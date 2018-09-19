---
title: '间接寻址运算符: * |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 01ceee27c58dc654b7022d3e9f56129e8914040b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110557"
---
# <a name="indirection-operator-"></a>间接寻址运算符：*

## <a name="syntax"></a>语法

```
* cast-expression
```

## <a name="remarks"></a>备注

一元间接寻址运算符 (<strong>\*</strong>) 取消引用指针; 即，它将一个指针值转换为左值。 间接寻址运算符的操作数必须是指向类型的指针。 间接寻址表达式的结果是从中派生指针类型的类型。 利用<strong>\*</strong>运算符在此上下文中的是不同于其含义为二元运算符，后者是乘法。

如果操作数指向函数，则结果是函数指示符。 如果它指向存储位置，则结果是指定存储位置的左值。

可以累计使用间接寻址运算符来取消引用指向指针的指针。 例如：

```cpp
// expre_Indirection_Operator.cpp
// compile with: /EHsc
// Demonstrate indirection operator
#include <iostream>
using namespace std;
int main() {
   int n = 5;
   int *pn = &n;
   int **ppn = &pn;

   cout  << "Value of n:\n"
         << "direct value: " << n << endl
         << "indirect value: " << *pn << endl
         << "doubly indirect value: " << **ppn << endl
         << "address of n: " << pn << endl
         << "address of n via indirection: " << *ppn << endl;
}
```

如果该指针的值无效，则结果是未定义的。 以下列表包含使指针值无效的一些最常见条件。

- 该指针为 null 指针。

- 该指针指定引用时不可见的本地项的地址。

- 该指针指定未针对所指向的对象类型正确对齐的地址。

- 该指针指定执行程序未使用的地址。

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Address-of 运算符：&](../cpp/address-of-operator-amp.md)<br/>
[间接寻址运算符和 Address-of 运算符](../c-language/indirection-and-address-of-operators.md)