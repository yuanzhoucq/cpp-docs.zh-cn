---
title: 编译器错误 C3340
ms.date: 11/04/2016
f1_keywords:
- C3340
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
ms.openlocfilehash: f4010870b84cbe2b8004eea24ab7735839b8c82b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753583"
---
# <a name="compiler-error-c3340"></a>编译器错误 C3340

“interface”：组件类“class”中的接口不能同时是“restricted”和“default”

[restricted](../../windows/restricted.md) 特性和 [default](../../windows/default-cpp.md) 特性是互相排斥的。

下面的示例生成 C3340：

```cpp
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
