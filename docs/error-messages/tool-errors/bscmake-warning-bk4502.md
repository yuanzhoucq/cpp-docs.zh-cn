---
title: "BSCMAKE 警告 BK4502 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs: C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 042aaf4c416bf88c87b3177c40cf3f1611385922
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE 警告 BK4502
截断。SBR 文件不在文件名中的 e  
  
 更新期间指定最初不是.bsc 文件的一部分的长度为零.sbr 文件。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  指定的文件名出错。  
  
2.  已删除的文件。 (错误[BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)结果。)  
  
3.  文件损坏，需要 BSCMAKE 可执行完整生成。