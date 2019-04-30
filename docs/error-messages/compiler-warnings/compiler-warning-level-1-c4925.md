---
title: 编译器警告（等级 1）C4925
ms.date: 11/04/2016
f1_keywords:
- C4925
helpviewer_keywords:
- C4925
ms.assetid: a4b206c0-016a-4f28-873a-bb8bb41bad50
ms.openlocfilehash: cb7b416fe15380dc914bd57152e8a0ce3618ee85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393501"
---
# <a name="compiler-warning-level-1-c4925"></a>编译器警告（等级 1）C4925

“method”：不能从脚本调用调度接口方法

脚本语言不能创建 VT_BYREF“in”参数，只能创建 VT_BYREF“out”参数。

解决此警告的另一种方法是不令该参数（在定义和实现中）为指针类型。

下面的示例生成 C4925：

```
// C4925.cpp
// compile with: /LD /W1
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[ module(name="Test")];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IDisp {
   [id(9)] void f([in] int*);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002")  ]
struct CDisp : IDisp {   // C4925
   void f(int*) {}
};
```