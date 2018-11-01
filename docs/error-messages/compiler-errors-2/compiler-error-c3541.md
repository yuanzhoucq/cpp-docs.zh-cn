---
title: 编译器错误 C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 356936ee09b75b6930840e015d00ccebb2fd8bc2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596373"
---
# <a name="compiler-error-c3541"></a>编译器错误 C3541

type: typeid 无法应用于包含 auto 的类型

[Typeid](../../windows/typeid-cpp-component-extensions.md)运算符不能应用于指定的类型，因为它包含`auto`说明符。

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
[typeid](../../windows/typeid-cpp-component-extensions.md)