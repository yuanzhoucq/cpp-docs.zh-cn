---
title: 编译器错误 C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: e32ffca067c3b25120301527e7a708d53001d541
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376245"
---
# <a name="compiler-error-c3136"></a>编译器错误 C3136

interface: COM 接口只能从另一个 COM 接口继承，不是 COM 接口 interface。

应用于一个接口[接口属性](../../windows/attributes/interface-attributes.md)继承自不是 COM 接口的接口。 COM 接口最终继承自`IUnknown`。 前面的接口属性的任何接口是 COM 接口。

下面的示例生成 C3136:

```
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```