---
title: "NMAKE 警告 U4007 | Microsoft Docs"
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
  - "U4007"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4007"
ms.assetid: 61ec0417-6961-43c1-ade8-f9d6e93289e9
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 警告 U4007
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

文件名“filename”太长；截断为 8.3  
  
 给定文件的基名称具有八个以上的字符，或者扩展名具有三个以上的字符。  NMAKE 将该名称截断为八个字符的基名和三个字符的扩展名。  
  
 如果您的文件系统支持长文件名，则将该名称括在双引号 \(**"**\) 内。