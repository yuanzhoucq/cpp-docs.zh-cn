---
title: "32 位 Windows 时间/日期格式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.time"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "32 位 Windows"
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 32 位 Windows 时间/日期格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件的时间和日期被分别存储，使用无符号整数作为位域。  文件的时间和日期打包如下：  
  
### 时间  
  
|Bit位置：|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|  
|------------|-----------------------|---------------------------|-----------------------|  
|长度：|5|6|5|  
|内容:|hours|分钟|2秒为增量|  
|值范围|0–23|0–59|0\-29 以 2 秒为间隔|  
  
### 日期  
  
|Bit位置：|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|  
|------------|-------------------------------|-------------------|-----------------------|  
|长度：|7|4|5|  
|内容:|year|month|天|  
|值范围|0–119|1–12|1–31|  
||\(相对于 1980\)|||  
  
## 请参阅  
 [全局常量](../c-runtime-library/global-constants.md)