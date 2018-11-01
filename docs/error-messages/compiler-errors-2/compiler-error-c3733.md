---
title: 编译器错误 C3733
ms.date: 11/04/2016
f1_keywords:
- C3733
helpviewer_keywords:
- C3733
ms.assetid: 0cc1a9fe-1400-4be3-b35a-16435cba7a5a
ms.openlocfilehash: 006f87691c6e0839115e2c02ab0d922aa95eaa93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501642"
---
# <a name="compiler-error-c3733"></a>编译器错误 C3733

event： 指定 COM 事件; 的语法不正确您是否忘记了 __interface？

COM 事件使用的不正确的语法。 若要解决此错误，请更改事件类型或更正语法以符合 COM 事件的规则。

下面的示例生成 C3733:

```
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[coclass, event_source(com), // change 'com' to 'native' to resolve
uuid("00000000-0000-0000-0000-000000000001")]
class A
{
   __event void func();   // C3733
};

int main()
{
}
```