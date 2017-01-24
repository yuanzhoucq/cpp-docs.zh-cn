---
title: "编译器错误 C2014 | Microsoft Docs"
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
  - "C2014"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2014"
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2014
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

预处理器命令必须作为第一个非空白空间启动  
  
 预处理器指令的 `#` 符号必须是非空白行上的第一个字符。  
  
 下面的示例生成 C2014：  
  
```  
// C2014.cpp  
int k; #include <stdio.h>   // C2014  
```  
  
 可能的解决方案：  
  
```  
// C2014b.cpp  
// compile with: /c  
int k;   
#include <stdio.h>  
```