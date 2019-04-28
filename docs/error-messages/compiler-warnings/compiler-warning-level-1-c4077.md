---
title: 编译器警告（等级 1）C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: 5171ee79c3afd32e847483568fbbf90222747509
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208345"
---
# <a name="compiler-warning-level-1-c4077"></a>编译器警告（等级 1）C4077

未知的 check_stack 选项

旧式 **check_stack** 杂注与未知的参数一起使用。 参数必须为 `+`、 `-`、 `(on)`、 `(off)`或为空。

编译器将忽略杂注，保持堆栈检查不变。

## <a name="example"></a>示例

```
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```