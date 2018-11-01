---
title: 编译器警告（等级 1）C4556
ms.date: 08/27/2018
f1_keywords:
- xml
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: 53261b97249340ce56ce6ae0f5cc0eab7e97a107
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538484"
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