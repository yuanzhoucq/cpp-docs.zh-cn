---
title: 链接器工具警告 LNK4099 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22764705b35b2e882c5a03e819c9812d084dc118
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4099"></a>链接器工具警告 LNK4099
PDB filename 找不到与对象/库 ' 或 'path';正在链接对象，如同没有调试信息  
  
 链接器无法找到.pdb 文件。 将其复制到包含的目录`object/library`。  
  
 若要查找的对象文件与关联的.pdb 文件的名称：  
  
1.  从库中，与提取的对象文件[lib](../../build/reference/lib-reference.md) **/提取：**`objectname`**.obj** `xyz` **.lib**。  
  
2.  检查包含的.pdb 文件的路径**dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**。  
  
 此外可以使用编译[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)，因此不需要使用，或者删除 pdb [/调试](../../build/reference/debug-generate-debug-info.md)链接器选项，如果你没有要链接的对象的.pdb 文件。