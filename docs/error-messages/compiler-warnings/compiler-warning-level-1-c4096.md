---
title: 编译器警告（等级1） C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 8f526b26eda4c02825d225aa007c6029cc4b03dd
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627076"
---
# <a name="compiler-warning-level-1-c4096"></a>编译器警告（等级1） C4096

"a"：接口不是 COM 接口;不会发送到 IDL

你可能打算用作 COM 接口的接口定义未定义为 COM 接口，因此不会将其发送到 IDL 文件。

请参阅表示接口是 COM 接口的列表属性的[接口特性](../../windows/attributes/interface-attributes.md)。

下面的示例生成 C4096：

```cpp
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