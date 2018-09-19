---
title: 资源编译器错误 RC1120 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f28e381d4eac0bfd1f010ef3919452635a1b96
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056997"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>资源编译器错误 RC1120

内存不足，请所需的字节数

资源编译器用尽了将存储在其堆中的项的存储。 通常这是让的符号太多的结果。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 增加 Windows 交换文件空间。 有关增加交换文件空间的详细信息，请参阅 Windows 帮助中的虚拟内存。

1. 消除不必要包含文件，尤其是不需要`#define`s 和函数原型。

1. 将当前文件拆分成两个或多个文件并将其单独编译。

1. 删除其他程序或系统，可能正在消耗了大量的内存运行驱动程序。