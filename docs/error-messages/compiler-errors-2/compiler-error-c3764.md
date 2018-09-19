---
title: 编译器错误 C3764 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3764
dev_langs:
- C++
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b57b9005eacc6e4a59adecc38b40027fffb5bcf1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096998"
---
# <a name="compiler-error-c3764"></a>编译器错误 C3764

override_function： 不能重写基类方法 base_class_function

编译器检测到格式不正确的重写。 例如，基类函数不是`virtual`。 有关详细信息，请参阅[重写](../../windows/override-cpp-component-extensions.md)。

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