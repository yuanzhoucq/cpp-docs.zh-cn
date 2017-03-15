---
title: "项目生成错误 PRJ0013 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0013"
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 项目生成错误 PRJ0013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

系统资源可能严重不足。无法创建启动生成所需的管道。  
  
 该错误指示系统资源不足。  若要解决该错误，请减少其他进程\/应用程序使用的系统资源。  
  
 如果你的安全级别不足以创建管道，也可能出现该错误（请参阅 [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)）。