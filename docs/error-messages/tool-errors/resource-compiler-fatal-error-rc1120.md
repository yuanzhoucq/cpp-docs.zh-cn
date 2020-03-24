---
title: 资源编译器错误 RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: 855a76ff63145695a7063944701d7acc684e0084
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173005"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>资源编译器错误 RC1120

内存不足，需的字节数

资源编译器在其堆中存储的项的存储空间不足。 这通常是由于符号过多而导致的。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 增加 Windows 交换文件空间。 有关增加交换文件空间的详细信息，请参阅 Windows 中的虚拟内存帮助。

1. 消除不必要的包含文件，特别是不需要的 `#define`s 和函数原型。

1. 将当前文件拆分为两个或多个文件，并分别编译它们。

1. 删除系统中运行的其他程序或驱动程序，这可能会占用大量内存。
