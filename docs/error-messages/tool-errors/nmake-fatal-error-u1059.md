---
title: "NMAKE 错误 U1059 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1059"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1059"
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 错误 U1059
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 : 从属项中缺少“}”  
  
 未正确指定从属项的搜索路径。  路径中存在空格或省略了右大括号 \(**}**\)。  
  
 从属项的目录指定语法为  
  
 **{**   
 ***directories* }dependent**  
  
 其中 `directories` 指定一个或多个路径，路径之间以分号 \(**;**\) 分隔。  不允许有空格。  
  
 如果宏替换了部分或全部搜索路径，则要确保宏展开中不存在空格。