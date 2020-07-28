---
title: 编译器错误 C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: 419aa8229e0fe60d391345556c5fbd8be17558d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214732"
---
# <a name="compiler-error-c2150"></a>编译器错误 C2150

> "*identifier*"：位域必须有 "int"、"带符号的 int" 或 "无符号 int" 类型

位域的基类型必须是 **`int`** 、 **`signed int`** 或 **`unsigned int`** 。

## <a name="example"></a>示例

此示例显示了你可能会遇到 C2150，以及如何解决此问题：

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```
