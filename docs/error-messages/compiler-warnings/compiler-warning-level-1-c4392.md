---
title: 编译器警告（等级1） C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: b19080f4a86267a48618a5f40d7576c07c96c18a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966110"
---
# <a name="compiler-warning-level-1-c4392"></a>编译器警告（等级1） C4392

"签名"：内部函数的参数数目不正确，应为 "number" 个参数

编译器内部函数的函数声明的参数数目不正确。 生成的图像可能无法正确运行。

若要修复此警告，请更正声明或删除声明，并只 #include 适当的标头文件。

下面的示例生成 C4392：

```cpp
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