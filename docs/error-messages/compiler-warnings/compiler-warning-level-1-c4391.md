---
title: 编译器警告（等级 1）C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: d9d1cebe08a6a163d76271ab001ec91b7cee82a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567123"
---
# <a name="compiler-warning-level-1-c4391"></a>编译器警告（等级 1）C4391

签名： 不正确的内部函数的返回类型预期 type

编译器内部函数的函数声明必须返回类型错误。 生成的映像可能无法正常运行。

若要解决此警告，请更正的声明，或删除该声明，只需 #include 相应的头文件。

下面的示例生成 C4391:

```
// C4391.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_load_ss(float *p);   // C4391

#ifdef  __cplusplus
}
#endif

int main()
{
}
```