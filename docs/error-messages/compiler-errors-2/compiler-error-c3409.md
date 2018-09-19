---
title: 编译器错误 C3409 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3409
dev_langs:
- C++
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 338a98adb45ee9fc8eb392853a5693d10a171940
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058830"
---
# <a name="compiler-error-c3409"></a>编译器错误 C3409

不允许空特性块

括号被解释为编译器[特性](../../windows/cpp-attributes-reference.md)找到块，但没有属性。

使用方括号作为 lambda 表达式定义的一部分时，编译器可能生成此错误。 当编译器无法确定是否方括号是定义的 lambda 表达式或特性块的一部分时，将发生此错误。 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 如果方括号是特性块的一部分：

   1. 提供在特性块中的一个或多个属性。

   1. 删除特性块。

1. 如果方括号是 lambda 表达式的一部分：

   1. 请确保在 lambda 表达式遵循有效的语法规则。

         有关 lambda 表达式语法的详细信息，请参阅[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。

    2.

## <a name="example"></a>示例

下面的示例生成 C3409。

```
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

```
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>请参阅

[attribute](../../windows/cpp-attributes-reference.md)<br/>
[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)