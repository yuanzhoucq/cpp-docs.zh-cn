---
title: "NMAKE 错误 U1051 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93c109bf723b3c4cf08e998a715fe8f6f33be466
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 错误 U1051
内存不足  
  
 NMAKE 耗尽了内存，包括虚拟内存，由于生成文件太大或太复杂。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  释放一些磁盘空间。  
  
2.  增加 Windows NT 分页文件或 Windows 交换文件的大小。  
  
3.  如果仅生成文件的部分正在使用，则将生成文件划分为单独的文件或使用**！如果**预处理指令来限制 NMAKE 必须处理量。 **！如果**指令包含**！如果**， `!IFDEF`， **！IFNDEF**， **！ELSE IF**， **！其他** `IFDEF`，和**！其他** `IFNDEF`。