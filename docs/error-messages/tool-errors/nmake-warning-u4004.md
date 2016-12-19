---
title: "NMAKE 警告 U4004 | Microsoft Docs"
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
  - "U4004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4004"
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 警告 U4004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

目标“targetname”的规则太多  
  
 通过使用单冒号 \(**:**\) 作为分隔符已为给定目标指定多个描述块。  NMAKE 已执行第一个描述块中的命令并忽略后面的块。  
  
 若要在多个依赖项中指定同一目标，请在每个依赖项行中使用双冒号 \(`::`\) 作为分隔符。