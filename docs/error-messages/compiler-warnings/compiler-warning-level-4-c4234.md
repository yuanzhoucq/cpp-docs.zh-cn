---
title: 编译器警告（等级 4）C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: c27f16f7d2933ca1860b304afa6e04f96f0687f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173902"
---
# <a name="compiler-warning-level-4-c4234"></a>编译器警告（等级 4）C4234

使用了非标准扩展：保留 "关键字" 关键字供将来使用

编译器尚未实现所使用的关键字。

此警告会自动提升为错误。 如果要修改此行为，请使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使 C4234 成为第4级警告问题，

```cpp
#pragma warning(2:4234)
```

在源代码文件中。
