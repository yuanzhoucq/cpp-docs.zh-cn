---
title: 编译器错误 C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: 84fa715c8bd567770f361552e203a37c44ffdde4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451046"
---
# <a name="compiler-error-c2414"></a>编译器错误 C2414

非法的操作数数目

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 操作码不支持所用操作数的数。 检查程序集语言参考手册以确定正确的操作数数目。

1. 较新的处理器支持具有不同数目的操作数的指令。 调整[/arch （最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md)选项以使用更高版本的处理器。