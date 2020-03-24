---
title: 编译器错误 C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 8ab2e0d152e4c123fa23512bc0111cebd070b3ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200857"
---
# <a name="compiler-error-c3409"></a>编译器错误 C3409

> 不允许空特性块

## <a name="remarks"></a>备注

方括号被编译器解释为[属性](../../windows/attributes-alphabetical-reference.md)块，但找不到任何属性。

当使用方括号作为 lambda 表达式定义的一部分时，编译器可能会生成此错误。 当编译器无法确定方括号是 lambda 表达式定义的一部分还是特性块的一部分时，会发生此错误。 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 如果方括号是特性块的一部分：

   1. 提供特性块中的一个或多个特性。

   1. 删除特性块。

1. 如果方括号是 lambda 表达式的一部分，请确保 lambda 表达式遵循有效的语法规则。

   有关 lambda 表达式语法的详细信息，请参阅[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。

## <a name="example"></a>示例

下面的示例生成 C3409。

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

## <a name="example"></a>示例

下面的示例生成 C3409，因为 lambda 表达式使用 `mutable` 规范，但不提供参数列表。 编译器无法确定方括号是 lambda 表达式定义的一部分还是属于特性块。

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>另请参阅

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)
