---
title: 编译器警告 （等级 1） C4651 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b516ef86372901d00dd20d94ed10d5e361bbab8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099451"
---
# <a name="compiler-warning-level-1-c4651"></a>编译器警告（等级 1）C4651

指定有关预编译标头而不是当前编译的定义

在生成预编译标头，但不是在此编译中，已指定的定义。

定义将有效内部预编译标头，而不是在代码的其余部分。

如果使用 /DSYMBOL 生成预编译标头，编译器将生成此警告，如果 /Yu 编译没有 /DSYMBOL。  向 /Yu 命令行添加 /DSYMBOL 可消除此警告。