---
title: "HUGE_VAL、_HUGE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_HUGE"
apilocation: 
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_HUGE"
  - "HUGE_VAL"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_HUGE 常量"
  - "HUGE_VAL 常量"
  - "double 值"
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# HUGE_VAL、_HUGE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <math.h>  
  
```  
  
## 备注  
 `HUGE_VAL` 是最大的可表示的双精度值。  当发生错误时，许多运行时算术函数返回该值。  某些函数中，返回`HUGE_VAL`。  `HUGE_VAL` 定义为 `_HUGE`，但是，运行时算术函数返回 `HUGE_VAL`。  在代码应使用 `HUGE_VAL`确保一致性。  
  
## 请参阅  
 [全局常量](../c-runtime-library/global-constants.md)