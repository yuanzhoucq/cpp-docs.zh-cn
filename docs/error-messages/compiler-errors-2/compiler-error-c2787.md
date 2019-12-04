---
title: 编译器错误 C2787
ms.date: 11/04/2016
f1_keywords:
- C2787
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
ms.openlocfilehash: 00f2097dc556055f0becf1d81d784c9126c66f63
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739592"
---
# <a name="compiler-error-c2787"></a>编译器错误 C2787

"identifier"：没有与此对象关联的 GUID

[__Uuidof](../../cpp/uuidof-operator.md)运算符使用附加了 GUID 的用户定义类型或此类用户定义类型的对象。 当参数是不带 GUID 的用户定义类型时，将发生此错误。

下面的示例生成 C2787：

```cpp
// C2787.cpp
#include <windows.h>
struct F {};

struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;

int main() {
   __uuidof(F);   // C2787
   __uuidof(F2);   // OK
}
```
