---
title: 编译器警告 C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: 6eaaa4c1f16e2ac2c5029511430a145fd9b943e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428335"
---
# <a name="compiler-warning-c4694"></a>编译器警告 C4694

> '*类*： 密封的抽象类不能有基类'*base_class*

一个抽象密封类不能继承自引用类型；一个密封抽象类既不能实现基类函数，也不能用作基类。

有关详细信息，请参阅[抽象](../../windows/abstract-cpp-component-extensions.md)，[密封](../../windows/sealed-cpp-component-extensions.md)，并[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)。

此警告被自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。

## <a name="example"></a>示例

以下示例生成 C4694。

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```