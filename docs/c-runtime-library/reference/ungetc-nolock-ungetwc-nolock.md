---
title: "_ungetc_nolock、_ungetwc_nolock | Microsoft Docs"
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
  - "_ungetwc_nolock"
  - "_ungetc_nolock"
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
  - "_ungettc_nolock"
  - "ungetwc_nolock"
  - "ungetc_nolock"
  - "_ungetc_nolock"
  - "_ungetwc_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ungetc_nolock 函数"
  - "_ungettc_nolock 函数"
  - "_ungetwc_nolock 函数"
  - "字符, 推送回流"
  - "ungetc_nolock 函数"
  - "ungettc_nolock 函数"
  - "ungetwc_nolock 函数"
ms.assetid: aa02d5c2-1be1-46d2-a8c4-b61269e9d465
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ungetc_nolock、_ungetwc_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个字符推入流中。  
  
## 语法  
  
```  
int _ungetc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _ungetwc_nolock(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### 参数  
 `c`  
 要推出的字符。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 如果成功，这些函数都返回一个字符参数 `c`*。*如果 `c` 不能推回，或者未读取字符，输入流未更改，并且 `_ungetc_nolock` 返回 `EOF`; `_ungetwc_nolock` 返回 `WEOF`。  如果 `stream` 为 `NULL`，返回 `EOF` 或 `WEOF`，并且 `errno` 设置为 `EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 这些函数分别为 `ungetc` 和 `ungetwc`的非锁定版本。  除了它们不由其他线程干扰保护，`_nolock` 后缀的版本相同。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE & 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-------------------------------|----------------|-------------------|  
|`_ungettc_nolock`|`_ungetc_nolock`|`_ungetc_nolock`|`_ungetwc_nolock`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ungetc_nolock`|\<stdio.h\>|  
|`_ungetwc_nolock`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)