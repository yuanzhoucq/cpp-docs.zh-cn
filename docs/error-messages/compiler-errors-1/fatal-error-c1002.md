---
title: 错误 C1002 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f08255484b11f9f5d87fb67ac8ac7b401d4f6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044140"
---
# <a name="fatal-error-c1002"></a>错误 C1002

在第 2 遍中编译器的堆空间不足

在第二个阶段，很可能是由于具有过多符号或复杂表达式的程序过程中，编译器用尽动态内存空间。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 将源文件划分为多个较小的文件。

1. 分解为较小的子表达式的表达式。

1. 删除其他程序或占用内存的驱动程序。