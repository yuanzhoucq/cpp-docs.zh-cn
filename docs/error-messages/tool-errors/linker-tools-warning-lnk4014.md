---
title: 链接器工具警告 LNK4014 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4014
dev_langs:
- C++
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fb86efbdc70342861a87a233ab687f7564cb48b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4014"></a>链接器工具警告 LNK4014
找不到成员对象"objectname"  
  
 找不到 LIB`objectname`库中。  
  
 **/删除**和 **/提取**选项都需要将被删除或复制到文件的成员对象的完整名称。 完整名称包含原始对象文件的路径。 若要查看的库中的成员对象的完整名称，使用 DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md)或 LIB [/列表](../../build/reference/managing-a-library.md)。