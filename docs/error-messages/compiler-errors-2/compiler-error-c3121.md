---
title: 编译器错误 C3121
ms.date: 11/04/2016
f1_keywords:
- C3121
helpviewer_keywords:
- C3121
ms.assetid: 1d3c7be4-d42d-4def-8d53-182c0c5cc237
ms.openlocfilehash: e5d5f85631dbbedcabce89c25d9af7a7a685342c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740918"
---
# <a name="compiler-error-c3121"></a>编译器错误 C3121

无法更改类 "class_name" 的 GUID

您尝试更改类 ID [__declspec （uuid）](../../cpp/uuid-cpp.md)。

例如，下面的代码生成 C3121：

```cpp
// C3121.cpp
[emitidl];
[module(name="MyLibrary")];

[coclass, uuid="00000000-0000-0000-0000-111111111111"]
class __declspec(uuid("00000000-0000-0000-0000-111111111112")) A   // C3121
{
};
int main()
{
}
```
