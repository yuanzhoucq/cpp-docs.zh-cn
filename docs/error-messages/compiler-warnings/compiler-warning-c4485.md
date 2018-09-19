---
title: 编译器警告 C4485 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4485
dev_langs:
- C++
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb83700bf8ca79960599d85ed3d335f80c9fc7f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117746"
---
# <a name="compiler-warning-c4485"></a>编译器警告 C4485

override_function： 匹配 ref 基类方法 base_class_function，但不是标记为 new 或 override;假定 new （和 virtual）

取值函数重写，无论`virtual`关键字、 基类访问器函数，但`override`或`new`说明符不是重写的函数签名的一部分。 添加`new`或`override`说明符来解决此警告。

请参阅[重写](../../windows/override-cpp-component-extensions.md)并[新 (新 vtable 中的槽）](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)有关详细信息。

C4485 始终作为错误发出。 使用[警告](../../preprocessor/warning.md)杂注来禁止显示 C4485。

## <a name="example"></a>示例

下面的示例生成 C4485

```
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