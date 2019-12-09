---
title: 编译器错误 C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 2f0ca98dc44a78adde378a0f80078ae30c590e11
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738812"
---
# <a name="compiler-error-c3199"></a>编译器错误 C3199

使用浮点 pragma 无效：在非精确模式下不支持异常

[Float_control](../../preprocessor/float-control.md)杂注用于指定 **/fp：精确**的[/fp](../../build/reference/fp-specify-floating-point-behavior.md)设置下的浮点异常模型。

下面的示例生成 C3199：

```cpp
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```
