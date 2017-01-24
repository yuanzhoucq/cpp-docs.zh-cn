---
title: "链接器工具错误 LNK2027 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2027"
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK2027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法解析的模块引用“module”  
  
 传递给链接器的文件在既未使用 **\/ASSEMBLYMODULE** 指定，又未直接传递给链接器的模块上具有依赖项。  
  
 若要解决 LNK2027 问题，请执行以下操作之一：  
  
-   不要向链接器传递具有模块依赖项的文件。  
  
-   使用 **\/ASSEMBLYMODULE** 指定模块。  
  
-   如果模块为安全的 .netmodule 中，模块直接传递给链接器。  
  
 有关更多信息，请参见[\/ASSEMBLYMODULE（向程序集添加 MSIL 模块）](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)和[用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。