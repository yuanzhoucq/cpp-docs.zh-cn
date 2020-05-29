---
title: 编译器警告 C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: c92f805eb2960336ed34f5da93b6c13f46bf15ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165140"
---
# <a name="compiler-warning-c4485"></a>编译器警告 C4485

"override_function"：匹配 ref 基类方法 "base_class_function"，但未标记为 "new" 或 "override";假定为 "new" （和 "virtual"）

取值函数重写（带有或不带 `virtual` 关键字）一个基类访问器函数，但 `override` 或 `new` 说明符不是重写函数签名的一部分。 添加 `new` 或 `override` 说明符以解决此警告。

有关详细信息，请参阅[override](../../extensions/override-cpp-component-extensions.md)和[new （vtable 中的新槽）](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) 。

C4485 始终作为错误发出。 使用[警告](../../preprocessor/warning.md)杂注取消 C4485。

## <a name="example"></a>示例

下面的示例生成 C4485

```cpp
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```
