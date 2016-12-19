---
title: "2.4 Work-sharing Constructs | Microsoft Docs"
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
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4 Work-sharing Constructs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的工作划分构造分配关联的语句执行在遇到该团队中的成员的。  的工作划分指令不生成新线程，，而在项的提示的屏障的工作划分构造。  
  
 的工作划分构造和 **障碍** 指令序列遇到的必须相同。团队的每个线程执行。  
  
 OpenMP 定义以下的工作划分，构造，并且在后面的节中所述:  
  
-   **为** 指令  
  
-   **部分** 指令  
  
-   **单个** 指令