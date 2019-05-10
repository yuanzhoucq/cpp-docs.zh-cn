---
title: 编译器错误 C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 934e980149ad893e6799b0ab119a148fc5652fdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402783"
---
# <a name="compiler-error-c3199"></a>编译器错误 C3199

使用浮点 pragma 无效： 在非精确模式下不支持异常

[Float_control](../../preprocessor/float-control.md)杂注用于指定的浮点异常模型下[/fp](../../build/reference/fp-specify-floating-point-behavior.md)而不设置 **/fp： 精确**。

下面的示例生成 C3199:

```
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```