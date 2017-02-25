---
title: "命令行警告 D9026 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9026"
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 命令行警告 D9026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

选项应用于整个命令行  
  
 指定文件名之后，在命令中指定选项。  该选项应用到了它前面的文件。  
  
 例如，在命令  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 中，将使用 \/G5 而不是默认的 \/G4 选项编译文件 VERDI.c。  
  
 该行为与某些以前版本中的行为不同，以前的版本只应用在文件名的前面指定的选项，从而导致用 \/G4 编译 VERDI.c，用 \/G5 编译 PUCCINI.c。