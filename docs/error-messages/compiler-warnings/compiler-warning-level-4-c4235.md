---
title: 编译器警告（等级 4）C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 3e3cb2e40ed42b24ee52252003b26ec09cd86710
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541764"
---
# <a name="compiler-warning-level-4-c4235"></a>编译器警告（等级 4）C4235

使用了非标准扩展：此体系结构不支持关键字 "关键字"

编译器不支持所使用的关键字。

此警告会自动提升为错误。 如果要修改此行为，请使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使 C4235 成为第2级警告，请使用以下代码行

```cpp
#pragma warning(2:4235)
```

在源代码文件中。