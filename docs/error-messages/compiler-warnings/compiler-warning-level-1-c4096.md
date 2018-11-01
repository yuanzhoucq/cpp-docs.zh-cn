---
title: 编译器警告 （等级 1） C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 287465e9a3f5681f459f0823a4409b0906309a55
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436545"
---
# <a name="compiler-warning-level-1-c4096"></a>编译器警告 （等级 1） C4096

a： 接口不是一个 COM 接口;不会发送到 IDL

您可能打算为 COM 接口的接口定义未被定义为 COM 接口，因此将不会发送到 IDL 文件。

请参阅[接口特性](../../windows/attributes/interface-attributes.md)指示接口是一个 COM 接口的列表属性。

下面的示例生成 C4096:

```
// C4096.cpp
// compile with: /W1 /LD
#include "windows.h"
[module(name="xx")];

// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct b : a
{
};   // C4096, remove coclass or uncomment object
```