---
title: 编译器错误 C3764
ms.date: 11/04/2016
f1_keywords:
- C3764
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
ms.openlocfilehash: 2570ee9abb148b919242de7786cd6fa91765286f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773575"
---
# <a name="compiler-error-c3764"></a>编译器错误 C3764

override_function： 不能重写基类方法 base_class_function

编译器检测到格式不正确的重写。 例如，基类函数不是`virtual`。 有关详细信息，请参阅[重写](../../extensions/override-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3764。

```
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

C3764 基类方法是显式时也会发生和名为重写。 下面的示例生成 C3764。

```
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