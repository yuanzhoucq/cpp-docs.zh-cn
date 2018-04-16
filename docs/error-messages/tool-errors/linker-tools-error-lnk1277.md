---
title: "链接器工具错误 LNK1277 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3606207afc197dc26ac0540d476b74f52c0dc0a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1277"></a>链接器工具错误 LNK1277
pgd （文件名） 中找不到对象记录  
  
 使用时[/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)，之一的输入的.lib、 def 或.obj 文件的路径是不同于在其找到它们期间 /ltcg: pginstrument 的路径。 这可能由得到解释 LIB 环境变量中的更改后 /ltcg: pginstrument。 输入文件的完整路径存储在.pgd 文件。  
  
 /Ltcg: pgoptimize 进行需要输入到 /ltcg: pginstrument 阶段相同。  
  
 若要解决此警告，请执行以下操作：  
  
-   运行 /ltcg: pginstrument，重做所有测试运行，并运行 /ltcg: pgoptimize。  
  
-   将 LIB 环境变量更改为运行 /ltcg: pginstrument 时。  
  
 不建议使用 /LTCG:PGUPDATE 解决 LNK1277。