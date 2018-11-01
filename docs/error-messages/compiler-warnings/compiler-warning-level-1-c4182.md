---
title: 编译器警告（等级 1）C4182
ms.date: 11/04/2016
f1_keywords:
- C4182
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
ms.openlocfilehash: 49e3e2f62b4be50d14cb8da3d776b4640be7160c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486107"
---
# <a name="compiler-warning-level-1-c4182"></a>编译器警告（等级 1）C4182

\#包括嵌套级别深度; 为 number可能的无限递归

由于嵌套的包含文件数量过多，编译器用尽了堆上的空间。 当包含文件包含在另一个包含文件中时，它就是嵌套的。

此消息是信息性消息，出现在错误 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)之前。