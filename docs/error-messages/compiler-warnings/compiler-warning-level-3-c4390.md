---
title: 编译器警告 （等级 3） C4390 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4390
dev_langs:
- C++
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83131119e360bcf8193c2d6c8ca5a3cd09341516
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054179"
---
# <a name="compiler-warning-level-3-c4390"></a>编译器警告（等级 3）C4390

';': 找到空的受控的语句;这是目的？

不包含指令的控制语句后找到一个分号。

如果您收到 C4390 宏，则应使用[警告](../../preprocessor/warning.md)杂注来禁用 C4390 中包含宏的模块。

下面的示例生成 C4390:

```
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```