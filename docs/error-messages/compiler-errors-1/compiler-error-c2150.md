---
title: 编译器错误 C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: a9c6465ef87c12135ad4e6709741f0027d8ea3c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175142"
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