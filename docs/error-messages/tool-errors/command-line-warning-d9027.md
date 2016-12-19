---
title: "命令行警告 D9027 | Microsoft Docs"
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
  - "D9027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9027"
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令行警告 D9027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

忽略源文件\<filename\>  
  
 CL.exe 忽略输入源文件。  
  
 在带有 \/c 选项的命令行上，\/Fo 选项与输出文件名之间存在空格，该空格可能导致此警告。  例如：  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 因为在 \/Fo 与 `output.obj,`之间存在空格，所以 CL.exe 将 `output.obj`作为输入文件的名称。  若要修复此问题，请删除该空格：  
  
```  
cl /c /Fooutput.obj input.c   
```