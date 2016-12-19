---
title: "CLOCKS_PER_SEC、CLK_TCK | Microsoft Docs"
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
  - "CLOCKS_PER_SEC"
  - "CLK_TCK"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CLK_TCK 常量"
  - "CLOCKS_PER_SEC"
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CLOCKS_PER_SEC、CLK_TCK
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <time.h>  
```  
  
## 备注  
 以秒计的时间是由 `clock` 函数返回的值，除以 `CLOCKS_PER_SEC`。  `CLK_TCK` 等效，但将过时。  
  
## 请参阅  
 [clock](../c-runtime-library/reference/clock.md)   
 [全局常量](../c-runtime-library/global-constants.md)