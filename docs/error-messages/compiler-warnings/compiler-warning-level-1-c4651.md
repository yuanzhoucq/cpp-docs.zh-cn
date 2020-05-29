---
title: 编译器警告（等级 1）C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: bc8131665c970c3b86bb1e84e39636ae8f93897b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199524"
---
# <a name="compiler-warning-level-1-c4651"></a>编译器警告（等级 1）C4651

为预编译标头（而不是针对当前编译）指定的 "定义"

定义是在生成预编译标头时指定的，而不是在此编译中。

定义将在预编译标头内有效，但不会在其余代码中生效。

如果预编译标头是使用/DSYMBOL 生成的，则在/Yu 编译没有/DSYMBOL. 的情况下，编译器将生成此警告。  将/DSYMBOL 添加到/Yu 命令行可以解决此警告。
