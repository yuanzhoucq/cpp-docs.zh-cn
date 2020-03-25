---
title: 错误 C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 78edf886f34665f996497abe323a0ea5d3800c2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204927"
---
# <a name="fatal-error-c1002"></a>错误 C1002

在第 2 遍中编译器的堆空间不足

编译器在第二次传递过程中用尽了动态内存空间，这可能是由于符号或复杂表达式太多而导致的。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 将源文件分为多个较小的文件。

1. 将表达式分解为更小的子表达式。

1. 删除消耗内存的其他程序或驱动程序。
