---
title: 编译器错误 C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: a61a69aca53f7f8996d0261a57b749930ecc01cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638342"
---
# <a name="compiler-error-c3842"></a>编译器错误 C3842

“函数”: 不支持在 WinRT 或托管类型的成员函数上使用“const”和“volatile”限定符

[const](../../cpp/const-cpp.md)并[易失性](../../cpp/volatile-cpp.md)不支持 Windows 运行时或托管的类型的成员函数上。

下面的示例生成 C3842：

```
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```