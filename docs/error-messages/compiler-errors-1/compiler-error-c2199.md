---
title: 编译器错误 C2199 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2199
dev_langs:
- C++
helpviewer_keywords:
- C2199
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 616b155ad0ca22c3eb45fd881a22ff36b5430f81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083647"
---
# <a name="compiler-error-c2199"></a>编译器错误 C2199

语法错误： 找到标识符 (在全局范围内 （是否使用声明？）

指定的上下文导致语法错误。 可能不正确的声明语法。

下面的示例生成 C2199:

```
// C2199.cpp
// compile with: /c
int j = int(1) int(1);   // C2199
int j = 1;   // OK
```