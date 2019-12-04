---
title: 编译器错误 C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: e9396b3bc5eea5d15366fc94ffa308d78754c31e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754389"
---
# <a name="compiler-error-c3246"></a>编译器错误 C3246

“class”: 无法从“type”继承，因为它已声明为“sealed”

标记为 [sealed](../../extensions/sealed-cpp-component-extensions.md) 的类不能为任何其他类的基类。

以下示例生成 C3246：

```cpp
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
