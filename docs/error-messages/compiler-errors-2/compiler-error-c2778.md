---
title: 编译器错误 C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 247aba1b4dfe6b6d6db1e2b8f46f2aa08abf1a79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739982"
---
# <a name="compiler-error-c2778"></a>编译器错误 C2778

__declspec （uuid （））中的 GUID 格式不正确

为[uuid](../../cpp/uuid-cpp.md)扩展属性提供的 GUID 不正确。

GUID 必须是十六进制数字的字符串，格式如下：

```cpp
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

`uuid` 扩展属性接受[CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring)识别的字符串（带或不带大括号分隔符）。

下面的示例生成 C2778：

```cpp
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```
