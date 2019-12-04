---
title: 编译器错误 C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: 499c31b0c02bd72695cd6118612609a70316f0ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755741"
---
# <a name="compiler-error-c3612"></a>编译器错误 C3612

"type"：密封类不能是抽象的

默认情况下，使用 `value` 定义的类型是密封的，除非它实现其基的所有方法，否则类是抽象的。 密封的抽象类既不能是基类，也不能被实例化。

有关更多信息，请参阅[类和结构](../../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3612：

```cpp
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```
