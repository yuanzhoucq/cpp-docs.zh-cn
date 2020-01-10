---
title: 编译器错误 C3001
ms.date: 11/04/2016
f1_keywords:
- C3001
helpviewer_keywords:
- C3001
ms.assetid: d0e03478-1b44-47e5-8f5b-70415fa1f8bc
ms.openlocfilehash: 737754eb314b577ac73e91a5aab1ad31773fc5f3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302206"
---
# <a name="compiler-error-c3001"></a>编译器错误 C3001

“error_text”: 应为 OpenMP 指令名称

`omp` 杂注后面必须跟有指令。

下面的示例生成 C3001：

```c
// C3001.c
// compile with: /openmp
int main()
{
   #pragma omp   // C3001 missing token
}
```
