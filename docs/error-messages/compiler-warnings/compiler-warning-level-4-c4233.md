---
title: 编译器警告（等级 4）C4233
ms.date: 10/25/2017
f1_keywords:
- C4233
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
ms.openlocfilehash: 361e00b7361aab51ea077d7e248503f3654e5e58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401054"
---
# <a name="compiler-warning-level-4-c4233"></a>编译器警告（等级 4）C4233

> 使用了非标准扩展:*关键字*关键字只能在C++，不 C

编译器将编译为 C 源代码而不是C++，而使用的关键字仅在有效的C++。 编译器会将源文件编译为 C 如果源代码文件的扩展名为.c 或使用[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。

此警告被自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使第 4 级警告问题 C4233，可以将此行添加到源代码文件上：

```cpp
#pragma warning(4:4233)
```
