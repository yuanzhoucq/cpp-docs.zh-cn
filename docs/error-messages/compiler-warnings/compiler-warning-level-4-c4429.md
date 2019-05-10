---
title: 编译器警告（等级 4）C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: d4eb7e7075c7adf418254e748f104a6d57c72741
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391525"
---
# <a name="compiler-warning-level-4-c4429"></a>编译器警告（等级 4）C4429

可能不完整或格式不正确通用字符名称

编译器检测到可能的格式不正确的通用字符名称的字符序列。 通用字符名称是`\u`跟四个十六进制数字或`\U`跟八个十六进制数字。

下面的示例生成 C4429:

```
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```