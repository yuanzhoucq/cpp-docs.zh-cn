---
title: 链接器工具错误 LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 091d4e173bfb2eff8ffee2b5c30647f4d5e3bc04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195365"
---
# <a name="linker-tools-error-lnk1106"></a>链接器工具错误 LNK1106

文件无效或磁盘已满：无法查找到位置

该工具无法在内存映射文件中读取或写入 `location`。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 磁盘已满。

   释放一些空间，并再次链接。

1. 尝试通过网络链接。

   某些网络不完全支持链接器使用的内存映射文件。 尝试链接本地磁盘。

1. 磁盘上的坏块。

   尽管操作系统和磁盘硬件应检测到这样的错误，但您可能希望运行磁盘检查程序。

1. 堆空间不足。

   有关详细信息，请参阅[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) 。
