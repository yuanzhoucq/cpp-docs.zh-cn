---
title: 编译器错误 C2640
ms.date: 11/04/2016
f1_keywords:
- C2640
helpviewer_keywords:
- C2640
ms.assetid: e4d137ab-ed1d-457c-9eec-b70d97f1b0b4
ms.openlocfilehash: 75acfa4d702b31052b7113117c71bf66ed9de149
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758237"
---
# <a name="compiler-error-c2640"></a>编译器错误 C2640

"identifier"： __based 修饰符在引用上非法

`__based` 修饰符只能用于指针。

下面的示例生成 C2640：

```cpp
// C2640.cpp
void f(int i) {
    void *vp;
    int _based(vp) &vr = I;  // C2640
}
```
