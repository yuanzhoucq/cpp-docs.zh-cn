---
title: "链接器工具警告 LNK4206 | Microsoft Docs"
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
  - "LNK4206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4206"
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4206
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未找到预编译的类型信息；未链接或覆盖“filename”；正在链接对象，就像没有调试信息一样  
  
 未在 LINK 命令中指定用 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 编译的给定对象文件，或者该文件被覆盖了。  
  
 出现此警告的一种常见情况是：用 \/Yc 编译的 .obj 在库中，而其中没有从您的代码到该 .obj 的符号引用。在这种情况下，链接器将不使用（或者看不到）.obj 文件。此时，应重新编译代码并对剩余的对象（不使用 \/Yc 编译的对象）使用 [\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)。