---
title: 编译器错误 C3291
ms.date: 11/04/2016
f1_keywords:
- C3291
helpviewer_keywords:
- C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
ms.openlocfilehash: eb98be3677de6c93fdb7bedf7c0d482115891697
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760135"
---
# <a name="compiler-error-c3291"></a>编译器错误 C3291

“default”: 不能作为 trivial 属性的名称

Trivial 属性不能命名为 `default`。 有关更多信息，请参见 [property](../../extensions/property-cpp-component-extensions.md) 。

## <a name="example"></a>示例

以下示例生成 C3291。

```cpp
// C3291.cpp
// compile with: /clr /c
ref struct C {
   property System::String ^ default;   // C3291
   property System::String ^ Default;   // OK
};
```
