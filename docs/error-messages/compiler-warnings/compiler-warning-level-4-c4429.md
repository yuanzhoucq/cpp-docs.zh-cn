---
title: 编译器警告（等级 4）C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: e814867278701be11b0158789f6373453aea75b8
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683239"
---
# <a name="compiler-warning-level-4-c4429"></a>编译器警告（等级 4）C4429

通用字符名称可能不完整或格式不正确

编译器检测到可能是格式不正确的通用字符名称的字符序列。 通用字符名称 `\u` 后跟四个十六进制数字，或者 `\U` 后跟8个十六进制数字。

下面的示例生成 C4429：

```cpp
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```