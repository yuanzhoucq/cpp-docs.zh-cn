---
title: 编译器错误 C3764
ms.date: 11/04/2016
f1_keywords:
- C3764
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
ms.openlocfilehash: 3ede846c9068978ad5d283e97b1c96d3527bf67c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757224"
---
# <a name="compiler-error-c3764"></a>编译器错误 C3764

"override_function"：不能重写基类方法 "base_class_function"

编译器检测到格式错误的重写。 例如，基类函数未 `virtual`。 有关详细信息，请参阅[override](../../extensions/override-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3764。

```cpp
// C3764.cpp
// compile with: /clr /c
public ref struct A {
   void g(int);
   virtual void h(int);
};

public ref struct B : A {
   virtual void g(int) override {}   // C3764
   virtual void h(int) override {}   // OK
};
```

## <a name="example"></a>示例

当基类方法显式和命名重写时，也会发生 C3764。 下面的示例生成 C3764。

```cpp
// C3764_b.cpp
// compile with: /clr /c
ref struct A {
   virtual void Test() {}
};

ref struct B : public A {
   virtual void Test() override {}
   virtual void Test2() = A::Test {}   // C3764
};
```
