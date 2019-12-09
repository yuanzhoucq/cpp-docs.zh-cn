---
title: 编译器错误 C3050
ms.date: 11/04/2016
f1_keywords:
- C3050
helpviewer_keywords:
- C3050
ms.assetid: ee090a0b-29cc-4215-a2f9-d82af79b8e82
ms.openlocfilehash: f8ab53974ac59de235a36e56991d2ef89f06be59
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761268"
---
# <a name="compiler-error-c3050"></a>编译器错误 C3050

“type1”：ref 类不能从“type1”继承

`System::ValueType` 不能作为引用类型的基类。

以下示例生成 C3050：

```cpp
// C3050.cpp
// compile with: /clr /LD
ref struct X : System::ValueType {};   // C3050
ref struct Y {};   // OK
```
