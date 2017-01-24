---
title: "NMAKE 警告 U4011 | Microsoft Docs"
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
  - "U4011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4011"
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 警告 U4011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“target”: 不是所有的依赖项都可用；未生成目标  
  
 给定目标的从属项不存在或已过期，并且用于更新从属项的命令返回一个非零退出代码。  \/K 选项已通知 NMAKE 继续处理该生成的不相关部分，并在 NMAKE 会话完成时发出退出代码 1。  
  
 对于未能创建或更新的每个从属项，该警告在警告 [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) 之后发出。