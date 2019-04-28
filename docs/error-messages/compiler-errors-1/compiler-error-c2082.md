---
title: 编译器错误 C2082
ms.date: 11/04/2016
f1_keywords:
- C2082
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
ms.openlocfilehash: 8bfb54dc91ef9132e3930e2c0799070f80f5cd0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338618"
---
# <a name="compiler-error-c2082"></a>编译器错误 C2082

形参“identifier”的重定义

已在函数体中重新声明了函数的形参。 若要解决此错误，请删除重新定义。

以下示例生成 C2082：

```
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```