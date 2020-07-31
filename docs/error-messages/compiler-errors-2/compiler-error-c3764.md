---
title: 编译器错误 C3764
ms.date: 11/04/2016
f1_keywords:
- C3764
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
ms.openlocfilehash: 657cb6598eedf8abd050b47c124c78c3a028509f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214498"
---
# <a name="compiler-error-c3764"></a>编译器错误 C3764

"override_function"：不能重写基类方法 "base_class_function"

编译器检测到格式错误的重写。 例如，基类函数不是 **`virtual`** 。 有关详细信息，请参阅[override](../../extensions/override-cpp-component-extensions.md)。

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
