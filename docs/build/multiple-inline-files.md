---
title: "多内联文件 | Microsoft Docs"
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
  - "内联文件, 多个 NMAKE"
  - "多内联文件"
  - "NMAKE 程序, 内联文件"
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多内联文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令可以创建多个内联文件。  
  
## 语法  
  
```  
  
      command << <<  
inlinetext  
<<[KEEP | NOKEEP]  
inlinetext  
<<[KEEP | NOKEEP]  
```  
  
## 备注  
 对于每个文件，指定一或多行内联文本，该文本后面要跟包含分隔符的结束行。  在第一个文件分隔行后面的行上开始第二个文件的文本。  
  
## 请参阅  
 [生成文件中的内联文件](../build/inline-files-in-a-makefile.md)