---
title: "_acmdln、_tcmdln、_wcmdln | Microsoft Docs"
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
  - "_wcmdln"
  - "_acmdln"
apilocation: 
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_acmdln"
  - "acmdln"
  - "_wcmdln"
  - "wcmdln"
  - "_tcmdln"
  - "tcmdln"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_acmdln 全局变量"
  - "_tcmdln 全局变量"
  - "_wcmdln 全局变量"
  - "acmdln 全局变量"
  - "tcmdln 全局变量"
  - "wcmdln 全局变量"
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _acmdln、_tcmdln、_wcmdln
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

内部 CRT 全局变量。  命令行。  
  
## 语法  
  
```  
char * _acmdln; wchar_t * _wcmdln;  #ifdef WPRFLAG    #define _tcmdln _wcmdln #else    #define _tcmdln _acmdln  
```  
  
## 备注  
 这些 CRT 内部变量将存储完整的命令行。  将在 CRT 的导出符号中公开它们，但不会在代码中使用它们。  `_acmdln` 将数据存储为字符字符串。  `_wcmdln` 将数据存储为宽字符字符串。  可将 `_tcmdln` 定义为 `_acmdln` 或  `_wcmdln`，具体取决于哪一个是合适的。  
  
## 请参阅  
 [全局变量](../c-runtime-library/global-variables.md)