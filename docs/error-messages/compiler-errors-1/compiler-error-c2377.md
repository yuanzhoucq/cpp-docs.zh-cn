---
title: 编译器错误 C2377
ms.date: 11/04/2016
f1_keywords:
- C2377
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
ms.openlocfilehash: a1e8c50f7e5d822571daeefffc93d3e8c572c01b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745494"
---
# <a name="compiler-error-c2377"></a>编译器错误 C2377

“identifier”：重定义；typedef 不能由任何其他符号重载

`typedef` 标识符被重新定义。

以下示例生成 C2377：

```cpp
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```
