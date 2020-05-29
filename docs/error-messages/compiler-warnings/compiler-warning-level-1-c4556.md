---
title: 编译器警告（等级 1）C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: 501d79a8a86fcd3e2d8ba08dc2f03488f9abb827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162304"
---
# <a name="compiler-warning-level-1-c4556"></a>编译器警告（等级 1）C4556

> 内部直接参数 "*value*" 的值超出了 "*lowerbound* - *受到上限约束*" 范围

## <a name="remarks"></a>备注

内部函数与硬件指令匹配。 硬件指令具有固定数目的位来对常量进行编码。 如果*值*超出范围，则将不会正确编码。 编译器会截断附加位。

## <a name="example"></a>示例

下面的示例生成 C4556：

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
