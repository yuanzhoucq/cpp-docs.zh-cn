---
title: 编译器警告（等级 1）C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: 1dc0c546509b17132358f432f6a781035a314a72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386416"
---
# <a name="compiler-warning-level-1-c4392"></a>编译器警告（等级 1）C4392

签名： 内部函数的参数数目不正确应有 number 参数

对象的编译器内部函数的函数声明包含的参数数目不正确。 生成的映像可能无法正常运行。

若要解决此警告，请更正的声明，或删除该声明，只需 #include 相应的头文件。

下面的示例生成 C4392:

```
// C4392.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_stream_pd(double *dp);   // C4392

#ifdef  __cplusplus
}
#endif

int main()
{
}
```