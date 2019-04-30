---
title: 资源编译器错误 RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: eff46ddee118c3355e548c73220b407db0561e36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374244"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>资源编译器错误 RC1120

内存不足，请所需的字节数

资源编译器用尽了将存储在其堆中的项的存储。 通常这是让的符号太多的结果。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 增加 Windows 交换文件空间。 有关增加交换文件空间的详细信息，请参阅 Windows 帮助中的虚拟内存。

1. 消除不必要包含文件，尤其是不需要`#define`s 和函数原型。

1. 将当前文件拆分成两个或多个文件并将其单独编译。

1. 删除其他程序或系统，可能正在消耗了大量的内存运行驱动程序。