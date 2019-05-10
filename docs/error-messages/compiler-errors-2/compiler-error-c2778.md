---
title: 编译器错误 C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 56c316ac971d0bdd1a0ca27ef8d4282acbe24779
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227671"
---
# <a name="compiler-error-c2778"></a>编译器错误 C2778

在 __declspec(uuid()) GUID 格式不正确

不正确的 GUID 提供给[uuid](../../cpp/uuid-cpp.md)扩展的特性。

GUID 必须为具有以下格式的十六进制数字的字符串：

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

`uuid`扩展的特性接受字符串识别[CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring)、 使用或不带括号分隔符。

下面的示例生成 C2778:

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```