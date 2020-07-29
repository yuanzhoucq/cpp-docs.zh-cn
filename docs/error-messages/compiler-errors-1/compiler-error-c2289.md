---
title: 编译器错误 C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 239552eb383197e57fcc6285cbf416c7c71c858b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216266"
---
# <a name="compiler-error-c2289"></a>编译器错误 C2289

多次使用同一类型限定符

类型声明或定义多次使用类型限定符（ **`const`** 、 **`volatile`** 、 **`signed`** 或 **`unsigned`** ），从而导致 ANSI 兼容性（**/za**）下出现错误。

下面的示例生成 C2286：

```cpp
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```
