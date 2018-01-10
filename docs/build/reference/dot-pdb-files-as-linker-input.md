---
title: ".用作链接器输入的 Pdb 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5acdc01a58cf0d501be5947cddf710d1b7c6d18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="pdb-files-as-linker-input"></a>用作链接器输入的 .Pdb 文件
对象 (.obj) 文件使用了 /Zi 选项编译包含的程序数据库 (PDB) 的名称。 未指定到链接器; 的对象的 PDB 文件名称链接使用嵌入的名称查找 PDB，如果需要。 这同样适用于可调试库; 中包含的对象可调试库的 PDB 必须可供随同库一起链接器。  
  
 链接还使用 PDB 来保存.exe 文件或.dll 文件的调试信息。 程序的 PDB 是输出文件和输入的文件，因为它重新生成程序时，链接更新 PDB。  
  
## <a name="see-also"></a>请参阅  
 [LINK 输入的文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)