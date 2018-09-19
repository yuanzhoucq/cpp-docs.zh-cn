---
title: 编译器错误 C2787 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2787
dev_langs:
- C++
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4096e5dbd5b885afe3dec136a111ec69a10784f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109127"
---
# <a name="compiler-error-c2787"></a>编译器错误 C2787

identifier： 没有 GUID 已与此对象关联

[__Uuidof](../../cpp/uuidof-operator.md)运算符采用与附加的 GUID 或用户定义类型的对象的用户定义的类型。 当参数是不具有 GUID 的用户定义的类型时，将出现此错误。

下面的示例生成 C2787:

```
// C2787.cpp
#include <windows.h>
struct F {};

struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;

int main() {
   __uuidof(F);   // C2787
   __uuidof(F2);   // OK
}
```