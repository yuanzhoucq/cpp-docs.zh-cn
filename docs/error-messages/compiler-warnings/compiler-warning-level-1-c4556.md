---
title: 编译器警告（等级 1）C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: c31602766261a8d6d0c4f0bb0a880ee34ee1ed45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397310"
---
# <a name="compiler-warning-level-1-c4556"></a>编译器警告（等级 1）C4556

> 内部即时参数的值*值*不在范围内'*lowerbound* - *upperbound*

## <a name="remarks"></a>备注

内部函数匹配硬件指令。 硬件指令具有固定的数量的位进行编码常量。 如果*值*是超出范围，它将不进行编码正确。 编译器将截断多余的位。

## <a name="example"></a>示例

下面的示例生成 C4556:

```cpp
// C4556.cpp
// compile with: /W1
// processor: x86 IPF
#include <xmmintrin.h>

void test()
{
   __m64 m;
   _m_pextrw(m, 5);   // C4556
}

int main()
{
}
```