---
title: 编译器警告（等级1） C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: ed2e6c10e35e53c6a67de9fecfce5da5ae429b93
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626671"
---
# <a name="compiler-warning-level-1-c4286"></a>编译器警告（等级1） C4286

"type1"：由基类（"type2"）在行号上捕获

指定的异常类型由上一个处理程序处理。 第二个 catch 的类型派生自第一个的类型。 基类捕获派生类的异常的异常。

## <a name="example"></a>示例

```cpp
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