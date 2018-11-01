---
title: 编译器警告（等级 1）C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: be02d330678eaab7f538ed092641f957bdcb01b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455206"
---
# <a name="compiler-warning-level-1-c4286"></a>编译器警告（等级 1）C4286

type1： 由基类 (type2) 在行号上捕获

指定的异常类型由上一个处理程序处理。 第二个 catch 的类型派生自的第一个类型。 异常的基类捕获异常派生的类。

## <a name="example"></a>示例

```
//C4286.cpp
// compile with: /W1
#include <eh.h>
class C {};
class D : public  C {};
int main()
{
    try
    {
        throw "ooops!";
    }
    catch( C ) {}
    catch( D ) {}  // warning C4286, D is derived from C
}
```