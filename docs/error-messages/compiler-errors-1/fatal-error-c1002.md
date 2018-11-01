---
title: 错误 C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 0588da99994be547742cc530ba435002a2d73359
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640500"
---
# <a name="fatal-error-c1002"></a>错误 C1002

在第 2 遍中编译器的堆空间不足

在第二个阶段，很可能是由于具有过多符号或复杂表达式的程序过程中，编译器用尽动态内存空间。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 将源文件划分为多个较小的文件。

1. 分解为较小的子表达式的表达式。

1. 删除其他程序或占用内存的驱动程序。