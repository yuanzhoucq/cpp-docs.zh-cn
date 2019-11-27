---
title: 编译器警告（等级 4）C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 63a22fed0832677837eb786268fc92946d295b79
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541774"
---
# <a name="compiler-warning-level-4-c4234"></a>编译器警告（等级 4）C4234

使用了非标准扩展：保留 "关键字" 关键字供将来使用

编译器尚未实现所使用的关键字。

此警告会自动提升为错误。 如果要修改此行为，请使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使 C4234 成为第4级警告问题，

```cpp
#pragma warning(2:4234)
```

在源代码文件中。