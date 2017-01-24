---
title: "NMAKE 警告 U4010 | Microsoft Docs"
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
  - "U4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4010"
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 警告 U4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“target”: 生成失败；已指定 \/K，正在继续...  
  
 给定目标的命令块中的命令返回非零退出代码。  \/K 选项已通知 NMAKE 继续处理该生成的不相关部分，并在 NMAKE 会话完成时发出退出代码 1。  
  
 如果给定目标本身是另一个目标的从属项，则在该警告之后 NMAKE 发出 [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) 警告。