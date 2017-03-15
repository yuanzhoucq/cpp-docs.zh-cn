---
title: "命令行警告 D9041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9041"
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 命令行警告 D9041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

搗alue  
  
 在 **\/wd**、**\/we**、**\/wo** 或 **\/wl** 命令行选项中添加了代码分析警告编号，但没有同时指定 **\/analyze** 命令行选项。  若要更正此错误，可添加 **\/analyze** 命令行选项，或者从相应的 **\/w** 命令行选项中移除无效的警告编号。  
  
## 示例  
 下面的命令行示例生成警告 D9041：  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 若要修复该警告，请添加 **\/analyze** 命令行选项。  如果您的编译器版本不支持 **\/analyze**，请从 **\/wd** 选项中移除无效的警告编号。  
  
## 请参阅  
 [命令行错误 D8000 到 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [编译器选项](../../build/reference/compiler-options.md)