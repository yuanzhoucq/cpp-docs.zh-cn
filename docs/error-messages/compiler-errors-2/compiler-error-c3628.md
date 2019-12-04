---
title: 编译器错误 C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 9976cb2425f8f855ffb2903c07de22822c781e20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755819"
---
# <a name="compiler-error-c3628"></a>编译器错误 C3628

"基类"：托管或 WinRTclasses 仅支持公共继承

尝试使用托管或 WinRT 类作为[私有](../../cpp/private-cpp.md)或[受保护](../../cpp/protected-cpp.md)的基类。 托管类或 WinRT 类只能用作具有[公共](../../cpp/public-cpp.md)访问权限的基类。

下面的示例生成 C3628，并演示如何修复此错误：

```cpp
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
