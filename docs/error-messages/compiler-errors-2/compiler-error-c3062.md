---
title: 编译器错误 C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: 6f4157db4a2a1b1864446a082deddc73df2e2fe9
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776363"
---
# <a name="compiler-error-c3062"></a>编译器错误 C3062

enum： 枚举数需要值，因为基础类型为 type

可以指定一个枚举的基础类型。 但是，某些类型需要您要将值分配到每个枚举器。

枚举的详细信息，请参阅[枚举类](../../extensions/enum-class-cpp-component-extensions.md)。

下面的示例生成 C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```