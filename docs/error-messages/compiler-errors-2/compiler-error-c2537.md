---
title: 编译器错误 C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 437727b334087aef496dbb0a1f3f1c8cf2b45458
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345589"
---
# <a name="compiler-error-c2537"></a>编译器错误 C2537

specifier： 非法的链接规范

可能的原因：

1. 不支持链接说明符。 支持"C"的链接说明符。

1. 一组重载函数中的多个函数的指定了"C"链接。 这是不允许的。

下面的示例生成 C2537:

```
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```