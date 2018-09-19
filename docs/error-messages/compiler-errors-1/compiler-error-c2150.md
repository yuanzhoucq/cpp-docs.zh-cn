---
title: 编译器错误 C2150 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef0920c98fe59fe5bca49bba4c62a486a61c0a55
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024705"
---
# <a name="compiler-error-c2150"></a>编译器错误 C2150

> '*标识符*： 位域必须具有类型 int、 signed 的 int 或 unsigned 的 int

位域的基类型必须是`int`， `signed int`，或`unsigned int`。

## <a name="example"></a>示例

此示例演示如何可能会遇到 C2150，以及如何修复此错误：

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```