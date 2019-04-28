---
title: 编译器错误 C2019
ms.date: 11/04/2016
f1_keywords:
- C2019
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
ms.openlocfilehash: 6e9e5bbca5da13fdfd4727d3b19aa3656689ce96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303705"
---
# <a name="compiler-error-c2019"></a>编译器错误 C2019

应为预处理器指令，却找到“character”

字符跟在`#`登录，但这不是预处理器指令的第一个字母。

下面的示例生成 C2019:

```
// C2019.cpp
#!define TRUE 1   // C2019
```

可能的解决方法：

```
// C2019b.cpp
// compile with: /c
#define TRUE 1
```