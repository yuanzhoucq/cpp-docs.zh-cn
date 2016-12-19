---
title: "_setmbcp | Microsoft Docs"
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
  - "_setmbcp"
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
  - "_setmbcp"
  - "setmbcp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_setmbcp 函数"
  - "多字节代码页"
  - "setmbcp 函数"
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _setmbcp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置新的多字节代码页。  
  
## 语法  
  
```  
int _setmbcp(  
   int codepage   
);  
```  
  
#### 参数  
 `codepage`  
 区域设置无关多例程的新代码页中。  
  
## 返回值  
 页代码如果设置成功，将返回 0。  如果无效代码页值为 `codepage`，返回 \-1 提供和代码页设置保持不变。  如果内存分配失败，将 `errno` 设置为 `EINVAL`。  
  
## 备注  
 `_setmbcp` 函数被指定新的多字节代码页。  默认情况下，运行时系统自动设置多字节代码页为系统默认 ANSI 代码页。  多字节代码页设置影响不是区域设置相关的所有多字节例程。  但是，可能会指示 `_setmbcp` 在当前区域设置代码页 \(请参见使用定义的清单常数和相关行为结果如下列表\)。  有关依赖于区域设置代码页而非多字节代码页多实例的列表，请参见 [Multibyte 字符序列的说明](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。  
  
 多字节代码页也影响处理受以下类型库运行库程序的多字节字符：  
  
||||  
|-|-|-|  
|[\_exec 函数](../../c-runtime-library/exec-wexec-functions.md)|[\_mktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)|[\_stat](../../c-runtime-library/reference/stat-functions.md)|  
|[\_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[\_spawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)|[\_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[\_makepath](../../c-runtime-library/reference/makepath-wmakepath.md)|[\_splitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)|[tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
  
 此外，多字节字符程序接收 `argv` 或 `envp` 参数的任何运行库程序类型库，当参数 \(如 `_exec` 和 `_spawn` 函数系列\) 根据多字节代码页处理这些字符串。  因此，这些例程受更改多字节代码页为 `_setmbcp` 调用的也会影响。  
  
 可以将 `codepage` 自变量设置为以下任何一个值。  
  
-   `_MB_CP_ANSI` 使用从操作系统获得的 ANSI 代码页在程序启动。  
  
-   `_MB_CP_LOCALE` 使用上一调用获取的当前区域设置的代码页 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   `_MB_CP_OEM` 使用从操作系统获得的 OEM 代码页在程序启动。  
  
-   `_MB_CP_SBCS` 使用单字节代码页。  在代码页设置为 `_MB_CP_SBCS`，则一例程 \(如 [\_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) 始终返回 false。  
  
-   其他有效的代码页的值，无论值是 OEM 或 ANSI、，其他运行系统支持的代码页 \(UTF\-7、UTF\-8，不支持。\)  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_setmbcp`|\<mbctype.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)