---
title: 编译器错误 C3198
ms.date: 11/04/2016
f1_keywords:
- C3198
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
ms.openlocfilehash: 61a3d14f9ad47edaa1e9b9f2b25d38b8dae7165c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243214"
---
# <a name="compiler-error-c3198"></a>编译器错误 C3198

使用浮点 pragma 无效： fenv_access 杂注仅在精确模式下运行

[fenv_access](../../preprocessor/fenv-access.md)下使用杂注[/fp](../../build/reference/fp-specify-floating-point-behavior.md)而不设置 **/fp： 精确**。

下面的示例生成 C3198:

```
// C3198.cpp
// compile with: /fp:fast
#pragma fenv_access(on)   // C3198
```