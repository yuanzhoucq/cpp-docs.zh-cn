---
title: 编译器警告 （等级 1） C4618 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4618
dev_langs:
- C++
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ff6080d6315156a1dbaeb89fae1d5cb10865405
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074261"
---
# <a name="compiler-warning-level-1-c4618"></a>编译器警告（等级 1）C4618

pragma 参数包括一个空字符串;忽略杂注

作为参数提供 null 字符串 **#pragma**。

杂注不带该参数已处理。

下面的示例生成 C4618:

```
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```