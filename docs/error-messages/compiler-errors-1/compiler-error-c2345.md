---
title: 编译器错误 C2345
ms.date: 11/04/2016
f1_keywords:
- C2345
helpviewer_keywords:
- C2345
ms.assetid: e1cc88b0-0223-4d07-975b-fa99956a82bd
ms.openlocfilehash: ceb2a835ca94399f27640628105afcde986af1b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479100"
---
# <a name="compiler-error-c2345"></a>编译器错误 C2345

align(value)：非法的对齐值

向 [align](../../cpp/align-cpp.md) 关键字传递了允许范围之外的值。

下面的代码生成 C2345

```
// C2345.cpp
// compile with: /c
__declspec(align(0)) int a;   // C2345
__declspec(align(1)) int a;   // OK
```