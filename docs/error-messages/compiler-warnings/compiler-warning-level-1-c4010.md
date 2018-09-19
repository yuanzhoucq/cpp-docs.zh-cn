---
title: 编译器警告 （等级 1） C4010 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52449689d329cee45cc69b63c315ce9335befbe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073085"
---
# <a name="compiler-warning-level-1-c4010"></a>编译器警告 （等级 1） C4010

单行注释包含行继续符

单行注释，引入的 / / 包含反斜杠 (\\) 用作行继续符。 编译器会考虑延续的下一行，并将其视为一条注释。

某些语法导向型编辑器并不表示在后是继续符为注释的行。 忽略语法突出显示的任何行的会导致此警告。

下面的示例生成 C4010:

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```