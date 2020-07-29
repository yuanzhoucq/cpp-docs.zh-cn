---
title: 编译器错误 C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: a041961e8a91832be67d8def8f2a6a3ef70906d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223390"
---
# <a name="compiler-error-c3540"></a>编译器错误 C3540

"type"： sizeof 不能应用于包含 "auto" 的类型

[Sizeof](../../cpp/sizeof-operator.md)运算符不能应用于所指示的类型，因为它包含 **`auto`** 说明符。

## <a name="example"></a>示例

下面的示例生成 C3540。

```cpp
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
[/Zc： auto （推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof 运算符](../../cpp/sizeof-operator.md)
