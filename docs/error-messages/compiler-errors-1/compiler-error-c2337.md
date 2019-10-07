---
title: 编译器错误 C2337
ms.date: 09/19/2019
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: bf9b3e782804add13aeaef0e6672d2dd66d193be
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158777"
---
# <a name="compiler-error-c2337"></a>编译器错误 C2337

> "*attribute-name*"：找不到属性

你的代码使用此上下文中不支持的属性。 或者，该特性在此版本的编译器中不可用。 若要解决此问题，请删除不支持的属性。

以下示例生成 C2337：

```cpp
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```
