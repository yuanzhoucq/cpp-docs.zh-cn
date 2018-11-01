---
title: 编译器警告（等级 4）C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 314ee068fb2be6148304360b0aaa3bd8029c283b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441010"
---
# <a name="compiler-warning-level-4-c4234"></a>编译器警告（等级 4）C4234

使用了非标准扩展: keyword 关键字保留供将来使用

编译器尚未实现您使用的关键字。

此警告被自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使 C4234 警告等级 4 问题，

```
#pragma warning(2:4234)
```

在你的源代码文件。