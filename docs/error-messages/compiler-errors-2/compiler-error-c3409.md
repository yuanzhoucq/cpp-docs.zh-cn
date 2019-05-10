---
title: 编译器错误 C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 24f107e0c1f74f95afc521c8a4c888a26a35c13a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173387"
---
# <a name="compiler-error-c3409"></a>编译器错误 C3409

> 不允许空特性块

## <a name="remarks"></a>备注

括号被解释为编译器[特性](../../windows/attributes-alphabetical-reference.md)找到块，但没有属性。

使用方括号作为 lambda 表达式定义的一部分时，编译器可能生成此错误。 当编译器无法确定是否方括号是定义的 lambda 表达式或特性块的一部分时，将发生此错误。 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 如果方括号是特性块的一部分：

   1. 提供在特性块中的一个或多个属性。

   1. 删除特性块。

1. 如果方括号是 lambda 表达式的一部分，请确保在 lambda 表达式遵循有效的语法规则。

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

下面的示例生成 C3409，因为 lambda 表达式使用`mutable`规范，但不提供的参数列表。 编译器无法确定是否方括号是定义的 lambda 表达式或特性块的一部分。

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>请参阅

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)