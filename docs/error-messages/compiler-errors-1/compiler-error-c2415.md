---
title: 编译器错误 C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: a0cdd528eca8ea267c62e6d44752d29ae16830c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205616"
---
# <a name="compiler-error-c2415"></a>编译器错误 C2415

不正确的操作数类型

操作码不使用此类型的操作数。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 操作码不支持使用的操作数。 检查汇编语言引用手册以确定正确的操作数。

1. 较新的处理器支持使用其他类型的指令。 调整[/arch （最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md)选项，以使用更高版本的处理器。
