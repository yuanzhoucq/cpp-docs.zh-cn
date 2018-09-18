---
title: 链接器工具错误 LNK1201 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1201
dev_langs:
- C++
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c133748f95846160e1387e31e023d9ce459b281
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055248"
---
# <a name="linker-tools-error-lnk1201"></a>链接器工具错误 LNK1201

写入程序数据库 filename; 时出错检查磁盘空间不足、 路径无效或没有足够的权限

链接无法写入到输出文件的程序数据库 (PDB)。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 文件已损坏。 删除 PDB 文件并重新链接。

1. 没有足够的磁盘空间来写入该文件。

1. 驱动器不可用，可能是由于网络问题。

1. 调试器上处于活动状态尝试链接的计划。

1. 堆空间不足。  请参阅[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)有关详细信息。