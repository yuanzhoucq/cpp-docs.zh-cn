---
title: 编译器错误 C3540 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6525812d56a82ce2f5d8cad7a63250c726ce5193
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103264"
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