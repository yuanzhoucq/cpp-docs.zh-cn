---
title: 编译器错误 C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 75862f3b80d617b607a7b3e735cb3e16e9a40bb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757379"
---
# <a name="compiler-error-c3136"></a>编译器错误 C3136

"interface"： COM 接口只能从另一个 COM 接口继承，"interface" 不是 COM 接口

应用了[接口特性](../../windows/attributes/interface-attributes.md)的接口继承自非 COM 接口的接口。 COM 接口最终继承自 `IUnknown`。 任何前面带有 interface 特性的接口都是一个 COM 接口。

下面的示例生成 C3136：

```cpp
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
