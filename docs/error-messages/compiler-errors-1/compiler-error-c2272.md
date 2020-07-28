---
title: 编译器错误 C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: e4163d68e0fbfea062279ba91e2c902855245e4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220387"
---
# <a name="compiler-error-c2272"></a>编译器错误 C2272

"function"：静态成员函数上不允许使用修饰符

**`static`** 成员函数由内存模型说明符（如[const](../../cpp/const-cpp.md)或[volatile](../../cpp/volatile-cpp.md)）声明，而成员函数不允许使用此类修饰符 **`static`** 。

下面的示例生成 C2272：

```cpp
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```
