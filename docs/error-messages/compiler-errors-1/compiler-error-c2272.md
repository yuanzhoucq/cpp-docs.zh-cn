---
title: 编译器错误 C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: 1a5a1e47a721cb6edd795012cc45943e63708936
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537418"
---
# <a name="compiler-error-c2272"></a>编译器错误 C2272

function： 静态成员函数上不允许修饰符

一个`static`成员函数声明和内存模型说明符，如[const](../../cpp/const-cpp.md)或[易失性](../../cpp/volatile-cpp.md)，且此类修饰符不允许对`static`成员函数。

下面的示例生成 C2272:

```
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```