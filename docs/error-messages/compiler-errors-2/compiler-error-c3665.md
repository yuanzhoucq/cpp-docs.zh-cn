---
title: 编译器错误 C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 4b0c019b2425b314f5b3503db41042d917283aa8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758172"
---
# <a name="compiler-error-c3665"></a>编译器错误 C3665

"析构函数"：重写说明符 "关键字" 在析构函数/终结器上不允许

在析构函数或终结器中使用了不允许使用的关键字。

例如，不能在析构函数或终结器上请求新的槽。  有关详细信息，请参阅[显式重写](../../extensions/explicit-overrides-cpp-component-extensions.md)和[析构函数和终结](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)器。

下面的示例生成 C3665：

```cpp
// C3665.cpp
// compile with: /clr
public ref struct R {
   virtual ~R() { }
   virtual void a() { }
};

public ref struct S : R {
   virtual ~S() new {}   // C3665
   virtual void a() new {}   // OK
};
```
