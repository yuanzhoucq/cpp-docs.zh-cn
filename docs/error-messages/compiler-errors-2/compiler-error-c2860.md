---
title: 编译器错误 C2860
ms.date: 11/04/2016
f1_keywords:
- C2860
helpviewer_keywords:
- C2860
ms.assetid: ccc83553-90ed-4e94-b5e9-38b58ae38e31
ms.openlocfilehash: 25ae5f0ffee659dee2e0ac388da207a5165ecc8e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214563"
---
# <a name="compiler-error-c2860"></a>编译器错误 C2860

"void" 不能是参数类型，"（void）" 除外

类型 **`void`** 不能用作带有其他参数的参数类型。

下面的示例生成 C2860：

```cpp
// C2860.cpp
// compile with: /c
void profunc1(void, int i);   // C2860
void func10(void);   // OK
```
