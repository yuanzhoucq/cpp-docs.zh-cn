---
title: "依赖项的搜索路径 | Microsoft Docs"
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
  - "依赖项, NMAKE"
  - "NMAKE 程序, 依赖项"
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 依赖项的搜索路径
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个依赖项有一个可选搜索路径，如以下所指定的：  
  
## 语法  
  
```  
{directory[;directory...]}dependent  
```  
  
## 备注  
 NMAKE 首先在当前目录中查找依赖项，然后按指定的顺序从其他目录中查找。  宏可以指定部分或全部搜索路径。  将目录名括在大括号 \({ }\) 内；用分号 \(;\) 分隔多个目录。  不允许使用空格或制表符。  
  
## 请参阅  
 [依赖项](../build/dependents.md)