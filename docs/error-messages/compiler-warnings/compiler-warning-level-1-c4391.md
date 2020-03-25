---
title: 编译器警告（等级 1）C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: 6dc5e2c7a40a276e225d030bc0340fb0bfe25bb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162720"
---
# <a name="compiler-warning-level-1-c4391"></a>编译器警告（等级 1）C4391

"签名"：不正确的内部函数返回类型，应为 "type"

编译器内部函数的函数声明具有错误的返回类型。 生成的图像可能无法正确运行。

若要修复此警告，请更正声明或删除声明，并只 #include 适当的标头文件。

下面的示例生成 C4391：

```cpp
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
