---
title: 编译器警告（等级 1）C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: fb9684b812e039bd37278f9f27db9225d0131f23
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626903"
---
# <a name="compiler-warning-level-1-c4077"></a>编译器警告（等级 1）C4077

未知的 check_stack 选项

旧式 **check_stack** 杂注与未知的参数一起使用。 参数必须为 `+`、 `-`、 `(on)`、 `(off)`或为空。

编译器将忽略杂注，保持堆栈检查不变。

## <a name="example"></a>示例

```cpp
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```