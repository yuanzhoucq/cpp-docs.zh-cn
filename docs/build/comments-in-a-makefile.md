---
title: "生成文件中的注释 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成文件, 注释"
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 生成文件中的注释
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在注释前放置一个数字符号 \(\#\)。  NMAKE 忽略从数字符号到下一个换行符之间的文本。  示例：  
  
```  
# Comment on line by itself  
OPTIONS = /MAP  # Comment on macro definition line  
  
all.exe : one.obj two.obj  # Comment on dependency line  
    link one.obj two.obj  
# Comment in commands block  
#   copy *.obj \objects  # Command turned into comment  
    copy one.exe \release  
  
.obj.exe:  # Comment on inference rule line  
    link $<  
  
my.exe : my.obj ; link my.obj  # Err: cannot comment this  
 # Error: # must be the first character  
.obj.exe: ; link $<  # Error: cannot comment this  
```  
  
 若要指定数字符号，请在它前面添一插入符号 \(**^**\)，如下所示：  
  
```  
DEF = ^#define  #Macro for a C preprocessing directive  
```  
  
## 请参阅  
 [生成文件的内容](../build/contents-of-a-makefile.md)