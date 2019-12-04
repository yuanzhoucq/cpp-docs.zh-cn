---
title: 编译器错误 C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5aa0d27b2d469f53ec521f587172398b7d4c2d1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761226"
---
# <a name="compiler-error-c2993"></a>编译器错误 C2993

"identifier"：非类型模板参数 "parameter" 的类型非法

不能声明具有结构或联合参数的模板。 使用指针将结构和联合作为模板参数传递。

下面的示例生成 C2993：

```cpp
// C2993.cpp
// compile with: /c
// C2993 expected
struct MyStruct {
   int a;char b;
};

template <class T, struct MyStruct S>   // C2993

// try the following line instead
// template <class T, struct MyStruct * S>
class CMyClass {};
```

在 Visual Studio .NET 2003：不再允许使用浮点非类型模板参数的情况下，也会生成此错误。 C++标准不允许浮点非类型模板参数。

如果它是函数模板，请使用函数参数传入浮点非类型模板参数（此代码将在 Visual Studio .NET 2003 和 visual Studio .NET 版本的 Visual C++studio 中有效）。 如果它是类模板，则没有简单的解决方法。

```cpp
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```
