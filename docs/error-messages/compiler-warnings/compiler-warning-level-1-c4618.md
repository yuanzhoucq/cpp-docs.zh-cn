---
title: 编译器警告（等级1） C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: fa9fc7d4a86ee686a9cd5d8d21412bd3346bcd80
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052569"
---
# <a name="compiler-warning-level-1-c4618"></a>编译器警告（等级1） C4618

pragma 参数包括空字符串;已忽略杂注

将空字符串作为参数提供给了 **#pragma**。

在没有参数的情况下处理杂注。

下面的示例生成 C4618：

```cpp
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```