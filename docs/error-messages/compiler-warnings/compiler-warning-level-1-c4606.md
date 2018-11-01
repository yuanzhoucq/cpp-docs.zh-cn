---
title: 编译器警告（等级 1）C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: e471ca3e478d1166b150e49bf25efa4b9d5803cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569268"
---
# <a name="compiler-warning-level-1-c4606"></a>编译器警告（等级 1）C4606

\#杂注警告: warning_number 被忽略;代码分析警告与警告等级无关

代码分析警告，仅`error`， `once`，并`default`支持与[警告](../../preprocessor/warning.md)杂注。

## <a name="example"></a>示例

下面的示例生成 C4606。

```
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```