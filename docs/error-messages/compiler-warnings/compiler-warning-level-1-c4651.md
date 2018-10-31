---
title: 编译器警告（等级 1）C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: 01e2472a547e73eda5fcc56952949a0d9611029f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434770"
---
# <a name="compiler-warning-level-1-c4651"></a>编译器警告（等级 1）C4651

指定有关预编译标头而不是当前编译的定义

在生成预编译标头，但不是在此编译中，已指定的定义。

定义将有效内部预编译标头，而不是在代码的其余部分。

如果使用 /DSYMBOL 生成预编译标头，编译器将生成此警告，如果 /Yu 编译没有 /DSYMBOL。  向 /Yu 命令行添加 /DSYMBOL 可消除此警告。