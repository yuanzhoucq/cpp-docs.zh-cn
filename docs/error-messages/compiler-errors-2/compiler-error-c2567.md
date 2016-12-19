---
title: "编译器错误 C2567 | Microsoft Docs"
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
  - "C2567"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2567"
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2567
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法打开“file”中的元数据，文件可能已删除或移动  
  
 编译器前端进程在某目录中找到了在源中引用的元数据文件（用 `#using`），而编译器后端进程找不到此文件。  有关更多信息，请参见[\#using 指令](../../preprocessor/hash-using-directive-cpp.md)。  
  
 如果在一台计算机上用 **\/c** 进行编译，然后在另一台计算机上尝试链接时代码生成，则可能导致 C2567。  有关更多信息，请参见 [\/LTCG（链接时代码生成）](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 它还可能指示您的计算机内存不足。  
  
 若要更正此错误，请确保对于生成过程的所有阶段，元数据文件都在同一个目录位置。