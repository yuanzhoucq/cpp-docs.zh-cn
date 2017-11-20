---
title: "BSCMAKE 错误 BK1506 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK1506
dev_langs: C++
helpviewer_keywords: BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c792f28b29ca9abf8594fbe6e351c4782b149a61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-error-bk1506"></a>BSCMAKE 错误 BK1506
无法打开文件 filename [: 原因]  
  
 BSCMAKE 无法打开文件。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  另一个进程锁定的文件。 如果`reason`指出**权限被拒绝**，浏览器可能正在使用该文件。 关闭浏览窗口，然后重试生成。  
  
2.  磁盘已满。  
  
3.  硬件错误。  
  
4.  指定的输出文件具有与现有子目录相同的名称。