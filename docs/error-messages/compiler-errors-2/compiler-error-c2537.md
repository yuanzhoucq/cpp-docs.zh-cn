---
title: 编译器错误 C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 0dfe9f88fcdfda1325150d480670777a4d42d896
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758627"
---
# <a name="compiler-error-c2537"></a>编译器错误 C2537

"说明符"：非法的链接规范

可能的原因：

1. 不支持链接说明符。 仅支持 "C" 链接说明符。

1. 为一组重载函数中的多个函数指定了 "C" 链接。 不允许这样做。

下面的示例生成 C2537：

```cpp
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```
