---
title: 编译器错误 C3340
ms.date: 11/04/2016
f1_keywords:
- C3340
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
ms.openlocfilehash: 1eff84ec133b55ddc3df98364c7d8542be398a69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644166"
---
# <a name="compiler-error-c3340"></a>编译器错误 C3340

“interface”：组件类“class”中的接口不能同时是“restricted”和“default”

[restricted](../../windows/restricted.md) 特性和 [default](../../windows/default-cpp.md) 特性是互相排斥的。

下面的示例生成 C3340：

```
// C3340.cpp
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface
{
   HRESULT f1();
};

[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f),
default(IMyIface),
source(IMyIface),restricted(IMyIface) ]
class CmyClass // C3340
{
};

int main()
{
}
```