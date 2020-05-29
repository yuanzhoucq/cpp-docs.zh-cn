---
title: 编译器警告（等级 1）C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: 5e6c945932699119f97bca2d3d118a03665f6f9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185875"
---
# <a name="compiler-warning-level-1-c4618"></a>编译器警告（等级 1）C4618

pragma 参数包括空字符串;已忽略杂注

将空字符串作为参数提供给了 **#pragma**。

在没有参数的情况下处理杂注。

下面的示例生成 C4618：

```cpp
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```
