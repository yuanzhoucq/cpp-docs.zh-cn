---
title: 编译器错误 C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 581aae7e1f979b3dd39caf2ce3d263fdb856c56a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221680"
---
# <a name="compiler-error-c3628"></a>编译器错误 C3628

base class： 托管或 WinRTclasses 只支持公共继承

尝试使用托管或 WinRT 类用作[私有](../../cpp/private-cpp.md)或[保护](../../cpp/protected-cpp.md)基类。 托管数组或 WinRT 类只能用作具有的基类[公共](../../cpp/public-cpp.md)访问。

下面的示例生成 C3628，并演示如何修复此错误：

```
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
