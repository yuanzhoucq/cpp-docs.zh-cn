---
title: "_findclose | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_findclose"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_findclose"
  - "findclose"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_findclose 函数"
  - "findclose 函数"
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _findclose
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

关闭指定搜索句柄并发释放相关资源。  
  
## 语法  
  
```  
int _findclose(   
   intptr_t handle   
);  
```  
  
#### 参数  
 `handle`  
 搜索句柄返回上一调用到 `_findfirst`。  
  
## 返回值  
 如果成功，`_findclose`返回 0 。  否则，返回 \-1 并将 `errno` 设置为 `ENOENT`，则表示找不到其他匹配的文件。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_findclose`|\<io.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [系统调用](../../c-runtime-library/system-calls.md)   
 [文件名搜索函数](../../c-runtime-library/filename-search-functions.md)