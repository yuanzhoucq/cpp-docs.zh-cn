---
title: 编译器错误 C3133
ms.date: 11/04/2016
f1_keywords:
- C3133
helpviewer_keywords:
- C3133
ms.assetid: 4a709405-b67b-4061-8a2a-19fa5fb34a2a
ms.openlocfilehash: 003befa97b033eec38d7187966da15e4a275f310
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760707"
---
# <a name="compiler-error-c3133"></a>编译器错误 C3133

特性不能应用于C++ varargs

未正确应用特性。 特性不能应用于表示变量参数的省略号。

有关更多信息，请参见 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3133。

```cpp
// C3133.cpp
// compile with: /clr /c
ref struct MyAttr: System::Attribute {};
void Func([MyAttr]...);   // C3133
void Func2([MyAttr] int i);   // OK
```
