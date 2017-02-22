---
title: "_initterm、_initterm_e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_initterm_e"
  - "_initterm"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_initterm_e"
  - "initterm"
  - "_initterm"
  - "initterm_e"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "initterm 函数"
  - "initterm_e 函数"
  - "_initterm 函数"
  - "_initterm_e 函数"
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# _initterm、_initterm_e
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内部方法指浏览函数指针表并初始化它们。  
  
 第一个指针是在表格中的起始位置，第二个指针在结束位置。  
  
## 语法  
  
```  
void __cdecl _initterm(  
   PVFV *,  
   PVFV *  
);  
  
int __cdecl _initterm_e(  
   PVFV *,  
   PVFV *  
);  
```  
  
## 返回值  
 如果初始化失败并抛出错误，显示一个非零的错误代码；如果未发生错误，显示0。  
  
## 备注  
 这些方法只在C\+\+程序初始化过程中被调用。  在程序中不能调用这些方法。  
  
 当这些方浏览函数输入表时，它们跳过 `NULL` 输入并继续。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)