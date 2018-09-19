---
title: 编译器警告 （等级 1） C4096 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4096
dev_langs:
- C++
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef2aaf3f37e9699547c3a85c55a2f72d4baab7a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047689"
---
# <a name="compiler-warning-level-1-c4096"></a>编译器警告 （等级 1） C4096

a： 接口不是一个 COM 接口;不会发送到 IDL

您可能打算为 COM 接口的接口定义未被定义为 COM 接口，因此将不会发送到 IDL 文件。

请参阅[接口特性](../../windows/interface-attributes.md)指示接口是一个 COM 接口的列表属性。

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