---
title: 编译器错误 C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 57e4145557272f76a890a356c79982346cd74d7e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037164"
---
# <a name="compiler-error-c3540"></a>编译器错误 C3540

type： 不能 sizeof 应用于包含 auto 的类型

[Sizeof](../../cpp/sizeof-operator.md)运算符不能应用于指定的类型，因为它包含`auto`说明符。

## <a name="example"></a>示例

下面的示例生成 C3540。

```
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)<br/>
[/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof 运算符](../../cpp/sizeof-operator.md)