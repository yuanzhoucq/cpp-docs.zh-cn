---
title: "链接器工具警告 LNK4205 | Microsoft Docs"
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
  - "LNK4205"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4205"
ms.assetid: d63b9d18-ef3c-4081-9d8d-93077dad13c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4205
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“filename”缺少引用模块的当前调试信息；正在链接对象，如同没有调试信息一样  
  
 .pdb 文件中有过期信息。  链接器将继续链接对象但不使用调试信息。  可能需要使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 选项重新编译对象文件。