---
title: 编译器错误 C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 40de7a7b1ede5e6dbbc20d2128b782c0ad6f798b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781024"
---
# <a name="compiler-error-c3665"></a>编译器错误 C3665

析构函数： 重写说明符 keyword 析构函数/终结器上不允许

使用析构函数或终结器上不允许的关键字。

例如，新的槽不能请求析构函数或终结器上。  有关详细信息，请参阅[显式重写](../../extensions/explicit-overrides-cpp-component-extensions.md)并[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

下面的示例生成 C3665:

```
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