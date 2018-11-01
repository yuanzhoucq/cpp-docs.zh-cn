---
title: 链接器工具错误 LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 7551e2f3f1efc90913981feb674f48aadb9ace51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619014"
---
# <a name="linker-tools-error-lnk1106"></a>链接器工具错误 LNK1106

无效的文件或磁盘已满： 无法查找到的位置

该工具无法读取或写入`location`内存映射文件中。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 磁盘已满。

   释放一些空间，并重新链接。

1. 尝试通过网络链接。

   某些网络不完全支持链接器使用的内存映射文件。 请尝试在本地磁盘上链接。

1. 在磁盘上的坏扇区。

   尽管操作系统和磁盘硬件应已检测到此类错误，您可能想要运行磁盘检查程序。

1. 堆空间不足。

   请参阅[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)有关详细信息。