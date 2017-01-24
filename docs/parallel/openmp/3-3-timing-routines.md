---
title: "3.3 Timing Routines | Microsoft Docs"
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
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.3 Timing Routines
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本节中介绍的函数支持一个可移植的墙时钟计时器:  
  
-   `omp_get_wtime` 函数返回 " 墙时钟时间。  
  
-   `omp_get_wtick` 函数返回连续的时钟计时周期之间的秒。