---
title: 编译器错误 C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: 881165a1100d1c8791ecd5f50eda6a2e9f1650eb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754909"
---
# <a name="compiler-error-c3842"></a>编译器错误 C3842

“函数”: 不支持在 WinRT 或托管类型的成员函数上使用“const”和“volatile”限定符

在 Windows 运行时或托管类型的成员函数上不支持[const](../../cpp/const-cpp.md)和[volatile](../../cpp/volatile-cpp.md) 。

下面的示例生成 C3842：

```cpp
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```
