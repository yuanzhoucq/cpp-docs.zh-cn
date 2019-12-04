---
title: 编译器错误 C2199
ms.date: 11/04/2016
f1_keywords:
- C2199
helpviewer_keywords:
- C2199
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
ms.openlocfilehash: 8bd6d587d28b8e7c190f7d3d58448fda501796cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758978"
---
# <a name="compiler-error-c2199"></a>编译器错误 C2199

语法错误：在全局范围内找到 "identifier （" （是否打算使用声明？）

指定的上下文导致语法错误。 可能存在不正确的声明语法。

下面的示例生成 C2199：

```cpp
// C2199.cpp
// compile with: /c
int j = int(1) int(1);   // C2199
int j = 1;   // OK
```
