---
title: 编译器警告（等级 1）C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 91e836c9bb606d7759206788d1e3abd63b293fa8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175306"
---
# <a name="compiler-warning-level-1-c4716"></a>编译器警告（等级 1）C4716

“function”必须返回值

给定函数未返回值。

只有返回类型为 void 的函数才能使用返回命令，而不会附带返回值。

如果调用此函数，则将返回未定义的值。

此警告会自动提升为错误。 如果要修改此行为，请使用[#pragma 警告](../../preprocessor/warning.md)。

下面的示例生成 C4716：

```cpp
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```
