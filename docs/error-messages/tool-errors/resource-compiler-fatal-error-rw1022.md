---
title: "资源编译器错误 RW1022 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RW1022
dev_langs: C++
helpviewer_keywords: RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e7ebd337ae2fc61342e814996a2a79b5c04f935c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-fatal-error-rw1022"></a>资源编译器错误 RW1022
**写入文件时出现 I/O 错误**  
  
 资源编译器无法写入文件。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  磁盘空间不足。 可用空间必须等于正在创建的可执行文件的大小的至少两倍。  
  
2.  卷为只读。  
  
3.  坏扇区。  
  
4.  共享冲突。