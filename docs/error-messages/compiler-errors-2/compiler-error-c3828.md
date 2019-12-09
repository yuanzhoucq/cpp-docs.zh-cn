---
title: 编译器错误 C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: 4b47ddbf0775cab2bd7214f68d1b4ed6e06e6eea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741698"
---
# <a name="compiler-error-c3828"></a>编译器错误 C3828

"object type"：在创建托管或 WinRTclasses 的实例时不允许使用位置参数

创建托管类型或 Windows 运行时类型的对象时，不能使用运算符[ref new、gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md)或[new](../../cpp/new-operator-cpp.md)的放置形式。

下列示例生成 C3828 并演示如何修复此错误：

```cpp
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```
