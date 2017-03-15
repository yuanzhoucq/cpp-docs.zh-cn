---
title: "链接器工具错误 LNK1302 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1302"
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 链接器工具错误 LNK1302
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只支持链接安全 .netmodule；无法链接文件 .netmodule  
  
 用户尝试调用 MSIL 链接时将.netmodule（使用 **\/LN** 编译）传递给了链接器。如果使用 **\/clr:safe** 对 C\+\+ 模块进行编译，则该模块对 MSIL 链接有效。  
  
 若要更正此错误，请使用 **\/clr:safe** 进行编译，以便启用 MSIL 链接或者将 **\/clr** 或 **\/clr:pure** .obj 文件传递给链接器而不是该模块。  
  
 有关更多信息，请参见  
  
-   [\/LN（创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)  
  
-   [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)