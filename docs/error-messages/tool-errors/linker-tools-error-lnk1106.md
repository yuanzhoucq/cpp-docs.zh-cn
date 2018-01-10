---
title: "链接器工具错误 LNK1106 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1106
dev_langs: C++
helpviewer_keywords: LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 793d788462a3a449c654c30ec874399a3bb85728
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1106"></a>链接器工具错误 LNK1106
无效的文件或磁盘已满： 找不到位置  
  
 该工具无法读取或写入`location`内存映射文件中。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  磁盘已满。  
  
     释放一些空间并重新链接。  
  
2.  在尝试通过网络链接。  
  
     某些网络不完全支持链接器使用的内存映射文件。 请尝试在您的本地磁盘上链接。  
  
3.  在你的磁盘上的坏扇区。  
  
     尽管操作系统和磁盘硬件应已检测到此类错误，你可能想要运行磁盘检查程序。  
  
4.  堆空间不足。  
  
     请参阅[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)有关详细信息。