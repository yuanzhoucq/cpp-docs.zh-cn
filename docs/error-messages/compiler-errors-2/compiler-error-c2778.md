---
title: 编译器错误 C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 98b5bf0a1315236f3ce96fd4b8c140ce1ab70a9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501040"
---
# <a name="compiler-error-c2778"></a>编译器错误 C2778

__declspec （uuid （））中的 GUID 格式不正确

为[uuid](../../cpp/uuid-cpp.md)扩展属性提供的 GUID 不正确。

GUID 必须是十六进制数字的字符串，格式如下：

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

`uuid`扩展属性接受 [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring) 识别的字符串（带或不带大括号分隔符）。

下面的示例生成 C2778：

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```