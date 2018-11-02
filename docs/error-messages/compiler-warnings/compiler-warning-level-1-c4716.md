---
title: 编译器警告（等级 1）C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 5ec0aea543053d699db7483df7dd7ea91b3af715
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594540"
---
# <a name="compiler-warning-level-1-c4716"></a>编译器警告（等级 1）C4716

“function”必须返回值

给定的函数未返回一个值。

只有函数返回类型为 void 可以使用不附带的返回值返回的命令。

此函数调用时，将返回未定义的值。

此警告被自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。

下面的示例生成 C4716:

```
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```