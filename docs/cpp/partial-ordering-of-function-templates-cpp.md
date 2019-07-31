---
title: 函数模板的部分排序 (C++)
ms.date: 07/30/2019
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 0c4f11b4b3e02504c4786ea34441362b542959d6
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682427"
---
# <a name="partial-ordering-of-function-templates-c"></a>函数模板的部分排序 (C++)

有多个与函数调用的自变量列表匹配的函数模板可用。 C++ 定义了函数模板的部分排序以指定应调用的函数。 由于有一些模板可能会视为专用化程度相同，因此排序只是部分的。

编译器从可能的匹配项中选择可用的专用化程度最高的模板函数。 例如, 如果一个函数模板采用类型`T` , 而另一个所采用`T*`的函数模板可用, 则`T*`认为该版本更为专用化。 只要参数是指针类型, `T`就优先使用泛型版本, 即使两者都是允许的匹配项。

通过以下过程可确定一个函数模板候选项是否更加专用化：

1. 考虑两个函数模板：T1 和 T2。

1. 将 T1 中的参数替换为假想的唯一类型 X。

1. 当 T1 中存在参数列表时，查看 T2 是否为该参数列表的有效模板。 忽略任何隐式转换。

1. 对 T1 和 T2 执行相反的过程。

1. 如果一个模板是另一个模板的有效模板参数列表, 但反之不成立, 则认为该模板不是专用于其他模板。 如果通过使用上一步, 两个模板都同时构成彼此的有效自变量, 则它们被视为同等专用化, 当你尝试使用它们时, 将会产生不明确的调用结果。

1. 使用以下规则：

   1. 针对特定类型的模板的专用化程度高于采用泛型类型参数的模板。

   1. 仅`T*`采用一个模板的专用化比只`T`采用一个模板更为专用, 因为`X*`假设类型是`T`模板参数的有效参数, 但`X`它不是有效的参数`T*`模板参数。

   1. `const T`比`T`更专业化, 因为`const X`是`T`模板参数的有效参数, `const T`但`X`它不是模板参数的有效参数。

   1. `const T*`比`T*`更专业化, 因为`const X*`是`T*`模板参数的有效参数, `const T*`但`X*`它不是模板参数的有效参数。

## <a name="example"></a>示例

下面的示例按标准中的规定工作:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

template <class T> void f(T) {
   printf_s("Less specialized function called\n");
}

template <class T> void f(T*) {
   printf_s("More specialized function called\n");
}

template <class T> void f(const T*) {
   printf_s("Even more specialized function for const T*\n");
}

int main() {
   int i =0;
   const int j = 0;
   int *pi = &i;
   const int *cpi = &j;

   f(i);   // Calls less specialized function.
   f(pi);  // Calls more specialized function.
   f(cpi); // Calls even more specialized function.
   // Without partial ordering, these calls would be ambiguous.
}
```

### <a name="output"></a>Output

```Output
Less specialized function called
More specialized function called
Even more specialized function for const T*
```

## <a name="see-also"></a>请参阅

[函数模板](../cpp/function-templates.md)
