---
title: 编译器错误 C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: fd6fdecd3a491ce5f068f4d51d413e6767aabe2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758692"
---
# <a name="compiler-error-c2272"></a>编译器错误 C2272

"function"：静态成员函数上不允许使用修饰符

`static` 成员函数上不允许使用内存模型说明符（如[const](../../cpp/const-cpp.md)或[volatile](../../cpp/volatile-cpp.md)）和此类修饰符来声明 `static` 成员函数。

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
