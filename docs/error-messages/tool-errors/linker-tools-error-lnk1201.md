---
title: 链接器工具错误 LNK1201 |Microsoft 文档
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
ms.openlocfilehash: 5ad83fecfe4df211cb7c5f301626454b5d2c9e47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298764"
---
# <a name="linker-tools-error-lnk1201"></a>链接器工具错误 LNK1201
错误写入到程序数据库 filename;检查有足够的磁盘空间、 路径无效或没有足够的权限  
  
 链接无法写入输出文件的程序数据库 (PDB)。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  文件已损坏。 删除 PDB 文件并重新链接。  
  
2.  没有足够的磁盘空间来写入文件。  
  
3.  驱动器不可用，可能是由于网络问题造成。  
  
4.  调试器上处于活动状态尝试链接程序。  
  
5.  堆空间不足。  请参阅[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)有关详细信息。