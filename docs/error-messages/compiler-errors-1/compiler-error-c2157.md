---
title: 编译器错误 C2157
ms.date: 11/04/2016
f1_keywords:
- C2157
helpviewer_keywords:
- C2157
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
ms.openlocfilehash: 2fa73148c9dbce843d3d1d075ca836f47b5ae074
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755884"
---
# <a name="compiler-error-c2157"></a>编译器错误 C2157

“function”：必须先声明才能用于杂注列表

在 [alloc_text](../../preprocessor/alloc-text.md) 杂注的函数列表中引用之前，未声明函数名。

下面的示例生成 C2157：

```cpp
// C2157.cpp
// compile with: /c
#pragma alloc_text( "func", func)   // C2157

// OK
extern "C" void func();
#pragma alloc_text( "func", func)
```
