---
title: 资源编译器错误 RC1002 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1002
dev_langs:
- C++
helpviewer_keywords:
- RC1002
ms.assetid: b43dfece-0dc3-4d0b-9d8f-509699b9ae80
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 886b44d0a51df10295428daa69c8ea358660fd25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1002"></a>资源编译器错误 RC1002
堆空间不足  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  增加 Windows 交换文件空间。 有关增加交换文件空间的详细信息，请参阅 Windows 帮助中的虚拟内存。  
  
2.  将当前文件拆分为较小的文件，然后单独对其进行编译。  
  
3.  删除其他程序或驱动程序的系统上运行。