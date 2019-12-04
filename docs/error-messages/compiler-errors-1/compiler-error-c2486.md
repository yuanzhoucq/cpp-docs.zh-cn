---
title: 编译器错误 C2486
ms.date: 11/04/2016
f1_keywords:
- C2486
helpviewer_keywords:
- C2486
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
ms.openlocfilehash: 75705bd8ecc850839e22fccbed1abf08687b3823
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743505"
---
# <a name="compiler-error-c2486"></a>编译器错误 C2486

仅在具有 "naked" 特性的函数中允许 "__LOCAL_SIZE"

在内联程序集函数中，名称 `__LOCAL_SIZE` 保留给用[naked](../../cpp/naked-cpp.md)特性声明的函数。

下面的示例生成 C2486：

```cpp
// C2486.cpp
// processor: x86
void __declspec(naked) f1() {
   __asm {
      mov   eax,   __LOCAL_SIZE
   }
}
void f2() {
   __asm {
      mov   eax,   __LOCAL_SIZE   // C2486
   }
}
```
