---
title: 错误 C1310
ms.date: 11/04/2016
f1_keywords:
- C1310
helpviewer_keywords:
- C1310
ms.assetid: ac48aa51-8023-42fe-b844-3f8bf228fbef
ms.openlocfilehash: 1b0fca9a5e453fd354a4efc6960a54386795ccf6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266423"
---
# <a name="fatal-error-c1310"></a>错误 C1310

按配置优化不能与 OpenMP 一起使用

你不能将 [/LTCG:PGI](../../build/reference/ltcg-link-time-code-generation.md) 与任何用 [/GL](../../build/reference/gl-whole-program-optimization.md)编译的模块进行链接。

以下示例生成 C1310：

```
// C1310.cpp
// compile with: /openmp /GL /link /LTCG:PGI
// C1310 expected
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 0; i++)
         --j;
   }
}
```