---
title: "_rmtmp | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_rmtmp"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "rmtmp"
  - "_rmtmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_rmtmp 函数"
  - "文件 [C++], 移除"
  - "文件 [C++], 临时"
  - "移除临时文件"
  - "rmtmp 函数"
  - "临时文件 [C++], 移除"
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rmtmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

删除临时文件。  
  
## 语法  
  
```  
  
int _rmtmp( void );  
```  
  
## 返回值  
 `_rmtmp` 返回关闭和删除的临时文件的数目。  
  
## 备注  
 `_rmtmp` 函数在当前目录中清除所有临时文件。  函数删除仅由 `tmpfile`创建删除的那些文件；仅在创建临时文件的相同目录下使用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_rmtmp`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
 请参阅 [tmpfile](../../c-runtime-library/reference/tmpfile.md) 示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)