---
title: "__uncaught_exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__uncaught_exception"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__uncaught_exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__uncaught_exception"
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# __uncaught_exception
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示是否抛出一个或多个异常，但未在相应的[try\-catch](../../cpp/try-throw-and-catch-statements-cpp.md) 语句的 `catch` 块中处理。  
  
## 语法  
  
```cpp  
bool __uncaught_exception(  
   );  
```  
  
## 返回值  
 在`try` 块中抛出的异常`true`，直至匹配的 `catch` 块被初始化；否则，返回 `false`。  
  
## 备注  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_\_uncaught\_exception|eh.h|  
  
## 请参阅  
 [try、throw 和 catch 语句 \(C\+\+\)](../../cpp/try-throw-and-catch-statements-cpp.md)