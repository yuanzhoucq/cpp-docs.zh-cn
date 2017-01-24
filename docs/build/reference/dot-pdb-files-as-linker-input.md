---
title: "用作链接器输入的 .Pdb 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 文件, 用作链接器输入"
  - "PDB 文件, 用作链接器输入"
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 用作链接器输入的 .Pdb 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 \/Zi 选项编译的对象 \(.obj\) 文件包含程序数据库 \(PDB\) 的名称。  不将对象的 PDB 文件名指定给链接器；如果需要，LINK 使用嵌入的名称查找 PDB。  这同样适用于库中包含的可调试对象；可调试库的 PDB 必须可用于链接器和该库。  
  
 LINK 还使用 PDB 保存 .exe 文件或 .dll 文件的调试信息。  程序的 PDB 既是输出文件也是输入文件，因为 LINK 在重新生成程序时更新 PDB。  
  
## 请参阅  
 [LINK 输入文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)