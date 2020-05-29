---
title: 编译器警告（等级1） C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 4f5a45339673b57f946f206e1eaff0d23ec6fee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163931"
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
