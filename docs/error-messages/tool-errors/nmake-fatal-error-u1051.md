---
title: NMAKE 错误 U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: 9c6b939c97f993e42049677292374377d825d474
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193675"
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 错误 U1051

内存不足

由于 makefile 太大或太复杂，NMAKE 内存用尽，包括虚拟内存。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 在磁盘上释放一些空间。

1. 增加 Windows NT 页面文件或 Windows 交换文件的大小。

1. 如果只使用部分生成文件，请将生成文件分成单独的文件或使用 **！如果**预处理指令限制 NMAKE 必须处理的量，则为。 **！IF**指令包括 **！如果**为，`!IFDEF`， **！IFNDEF**、 **！否则，IF**， **！ELSE** `IFDEF`和 **！否则**`IFNDEF`。
