---
title: "_get_current_locale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_current_locale"
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
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_current_locale"
  - "__get_current_locale"
  - "_get_current_locale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__get_current_locale 函数"
  - "_get_current_locale 函数"
  - "get_current_locale 函数"
  - "区域设置, 获取相关信息"
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _get_current_locale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取表示当前区域设置的区域设置对象。  
  
## 语法  
  
```  
_locale_t _get_current_locale(void);  
```  
  
## 返回值  
 表示当前区域设置的区域设置对象。  
  
## 备注  
 `_get_current_locale` 函数获取线程的当前设置的区域设置并返回表示该区域设置的区域设置对象。  
  
 `__get_current_locale`函数之前的名字\(带有两个前导下划线\)已弃用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_current_locale`|\<locale.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 无等效项。  
  
## 请参阅  
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)