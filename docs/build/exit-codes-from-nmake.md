---
title: "从 NMAKE 退出代码 | Microsoft Docs"
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
helpviewer_keywords: 
  - "退出代码"
  - "NMAKE 程序, 退出代码"
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 从 NMAKE 退出代码
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE 返回下列退出代码：  
  
|代码|含义|  
|--------|--------|  
|0|无错误（可能是警告）|  
|1|不完整的生成（只在使用 \/K 选项时发出）|  
|2|程序错误，可能由于下列原因之一：|  
||-   生成文件中的语法错误|  
||-   来自命令的错误或退出代码|  
||-   被用户中断|  
|4|系统错误 — 内存不足|  
|255|目标不是最新的（只在使用 \/Q 选项时发出）|  
  
## 请参阅  
 [运行 NMAKE](../build/running-nmake.md)