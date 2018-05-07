---
title: 链接器工具错误 LNK1277 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec8f00793fcda748c60d9d8ea775611e3d025cd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1277"></a>链接器工具错误 LNK1277
pgd （文件名） 中找不到对象记录  
  
 使用时[/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)，之一的输入的.lib、 def 或.obj 文件的路径是不同于在其找到它们期间 /ltcg: pginstrument 的路径。 这可能由得到解释 LIB 环境变量中的更改后 /ltcg: pginstrument。 输入文件的完整路径存储在.pgd 文件。  
  
 /Ltcg: pgoptimize 进行需要输入到 /ltcg: pginstrument 阶段相同。  
  
 若要解决此警告，请执行以下操作：  
  
-   运行 /ltcg: pginstrument，重做所有测试运行，并运行 /ltcg: pgoptimize。  
  
-   将 LIB 环境变量更改为运行 /ltcg: pginstrument 时。  
  
 不建议使用 /LTCG:PGUPDATE 解决 LNK1277。