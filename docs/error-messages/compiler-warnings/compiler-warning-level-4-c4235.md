---
title: 编译器警告（等级 4）C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 80ad388b26b2b972aa1301c1f335d0361a75f15f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401041"
---
# <a name="compiler-warning-level-4-c4235"></a>编译器警告（等级 4）C4235

使用了非标准扩展: keyword 关键字不支持此体系结构

编译器不支持您使用的关键字。

此警告被自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使 C4235 等级 2 警告，可使用以下代码行

```
#pragma warning(2:4235)
```

在你的源代码文件。