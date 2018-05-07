---
title: BSCMAKE 错误 BK1506 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1506
dev_langs:
- C++
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e19ec77818c8017387519b03e400c09d47021bc5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-error-bk1506"></a>BSCMAKE 错误 BK1506
无法打开文件 filename [: 原因]  
  
 BSCMAKE 无法打开文件。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  另一个进程锁定的文件。 如果`reason`指出**权限被拒绝**，浏览器可能正在使用该文件。 关闭浏览窗口，然后重试生成。  
  
2.  磁盘已满。  
  
3.  硬件错误。  
  
4.  指定的输出文件具有与现有子目录相同的名称。