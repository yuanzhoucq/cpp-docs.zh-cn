---
title: 编译器错误 C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 03361fa3e8d4ecb9647d354dd402a9f2b0865eb6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037680"
---
# <a name="compiler-error-c3541"></a>编译器错误 C3541

type: typeid 无法应用于包含 auto 的类型

[Typeid](../../extensions/typeid-cpp-component-extensions.md)运算符不能应用于指定的类型，因为它包含`auto`说明符。

## <a name="example"></a>示例

下面的示例生成 C3541。

```
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)<br/>
[/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)