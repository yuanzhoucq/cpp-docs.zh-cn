---
title: 编译器警告 （等级 1） C4606 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4606
dev_langs:
- C++
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcdaba046f495dc3a29a7c9228edc561674f568f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035989"
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