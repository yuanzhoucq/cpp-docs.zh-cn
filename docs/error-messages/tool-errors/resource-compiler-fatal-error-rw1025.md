---
title: "资源编译器错误 RW1025 | Microsoft Docs"
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
  - "RW1025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW1025"
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RW1025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

远堆内存不足  
  
 检查内存驻留软件，该软件可能占用太多空间。  使用 CHKDSK 程序查看还有多少内存。  
  
 如果您正在创建一个大型资源文件，则将该资源脚本拆分为两个文件。  创建两个 .res 文件之后，使用 MS\-DOS 命令行将这两个文件联接在一起：  
  
```  
copy first.res /b + second.res /b full.res  
```