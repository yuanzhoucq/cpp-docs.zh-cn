---
title: 编译器警告（等级 1）C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: 4da60194deaeac3c79f8c3e9be3bd87d91bc7ca2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386351"
---
# <a name="compiler-warning-level-1-c4730"></a>编译器警告（等级 1）C4730

main： 混合 _m64 和浮点表达式可能会导致不正确的代码

函数使用[__m64](../../cpp/m64.md)并**float**/**double**类型。 因为 MMX 和浮点寄存器都共享相同的物理寄存器空间 （不能同时使用），使用`__m64`并**float**/**double**中相同的类型函数可能会导致数据损坏，可能会导致异常。

若要安全地使用`__m64`类型和浮点类型的相同函数中，使用一种类型的每个指令应该分隔 **_m_empty()** （适用于 MMX) 或 **_m_femms （)** （适用于 3DNow ！)内部函数。

下面的示例生成 C4730:

```
// C4730.cpp
// compile with: /W1
// processor: x86
#include "mmintrin.h"

void func(double)
{
}

int main(__m64 a, __m64 b)
{
   __m64 m;
   double f;
   f = 1.0;
   m = _m_paddb(a, b);
   // uncomment the next line to resolve C4730
   // _m_empty();
   func(f * 3.0);   // C4730
}
```