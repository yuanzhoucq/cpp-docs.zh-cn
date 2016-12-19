---
title: "创建 .Sbr 文件 | Microsoft Docs"
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
  - ".sbr 文件"
  - "BSCMAKE, 输入文件"
  - "浏览器信息中的本地符号"
  - "SBR 文件"
  - "源浏览器文件"
  - "symbols"
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 创建 .Sbr 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

BSCMAKE 的输入文件是 .sbr 文件。  编译器为编译的每个对象文件 \(.obj\) 创建一个 .sbr 文件。  生成或更新浏览信息文件时，项目的所有 .sbr 文件在磁盘上都必须可用。  
  
 若要创建包含所有可能信息的 .sbr 文件，请指定 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)。  
  
 若要创建不包含本地符号的 .sbr 文件，请指定 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)。  如果 .sbr 文件包含本地符号，仍然可以通过使用 BSCMAKE 的 [\/El 选项](../../build/reference/bscmake-options.md)`.`从 .bsc 文件中省略这些符号。  
  
 不用执行完全编译便可以创建 .sbr 文件。  例如，如果指定 \/FR 或 \/Fr，则可以指定编译器的 \/Zs 选项来执行语法检查并且仍然生成 .sbr 文件。  
  
 如果首先压缩 .sbr 文件以移除未引用的定义，则生成过程的效率会更高。  编译器自动压缩 .sbr 文件。  
  
## 请参阅  
 [生成 .Bsc 文件](../../build/reference/building-a-dot-bsc-file.md)