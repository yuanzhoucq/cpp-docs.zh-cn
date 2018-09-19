---
title: 编译器错误 C3062 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95f2e58cada0b1b825fb0f065b461db6350de9fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067163"
---
# <a name="compiler-error-c3062"></a>编译器错误 C3062

enum： 枚举数需要值，因为基础类型为 type

可以指定一个枚举的基础类型。 但是，某些类型需要您要将值分配到每个枚举器。

枚举的详细信息，请参阅[枚举类](../../windows/enum-class-cpp-component-extensions.md)。

下面的示例生成 C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```