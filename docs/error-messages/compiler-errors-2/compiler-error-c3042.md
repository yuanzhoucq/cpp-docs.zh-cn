---
title: 编译器错误 C3042 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3042
dev_langs:
- C++
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36fde6251244582a0626c80aa673ed6dd0e559d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045209"
---
# <a name="compiler-error-c3042"></a>编译器错误 C3042

“copyprivate”和“nowait”子句不能同时出现在 OpenMP“directive”指令中

[Copyprivate](../../parallel/openmp/reference/copyprivate.md) 和 [nowait](../../parallel/openmp/reference/nowait.md) 子句在指定的指令上彼此排斥。 若要修复此错误，请删除 `copyprivate` 或 `nowait` 子句之一或两者一起删除。

以下示例生成 C3042：

```
// C3042.cpp
// compile with: /openmp /c
#include <stdio.h>
#include "omp.h"

double d;

int main() {
    #pragma omp parallel private(d)
   {
      #pragma omp single copyprivate(d) nowait   // C3042
      {
      }
   }
}
```