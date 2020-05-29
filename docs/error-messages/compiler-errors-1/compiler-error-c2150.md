---
title: 编译器错误 C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: 57c21f7ee9435220a9ca0b50bb85567506b6ad3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207215"
---
# <a name="compiler-error-c2150"></a>编译器错误 C2150

> "*identifier*"：位域必须有 "int"、"带符号的 int" 或 "无符号 int" 类型

位域的基类型需要是 `int`、`signed int`或 `unsigned int`。

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
