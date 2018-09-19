---
title: 编译器错误 C3136 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0439aa157a683065ccf7fff5b5f9d6d4d85e2f12
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054215"
---
# <a name="compiler-error-c3136"></a>编译器错误 C3136

interface: COM 接口只能从另一个 COM 接口继承，不是 COM 接口 interface。

应用于一个接口[接口属性](../../windows/interface-attributes.md)继承自不是 COM 接口的接口。 COM 接口最终继承自`IUnknown`。 前面的接口属性的任何接口是 COM 接口。

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