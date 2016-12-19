---
title: "_free_locale | Microsoft Docs"
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
  - "_free_locale"
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
  - "__free_locale"
  - "free_locale"
  - "_free_locale"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__free_locale 函数"
  - "_free_locale 函数"
  - "free_locale 函数"
  - "区域设置, 释放"
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _free_locale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

释放一个区域设置对象。  
  
## 语法  
  
```  
void _free_locale(  
   _locale_t locale  
);  
```  
  
#### 参数  
 `locale`  
 区域设置对象的释放。  
  
## 备注  
 `_free_locale` 函数通过调用 `_get_current_locale` 或 `_create_locale`释放获取的区域设置对象。  
  
 `__free_locale`函数之前的名字\(带有两个前导下划线\)已弃用。  
  
## 要求  
  
|`Routine`|必需的标头|  
|---------------|-----------|  
|`_free_locale`|\<locale.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 无等效项。  
  
## 请参阅  
 [\_get\_current\_locale](../../c-runtime-library/reference/get-current-locale.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)