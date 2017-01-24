---
title: "_creat、_wcreat | Microsoft Docs"
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
  - "_creat"
  - "_wcreat"
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
  - "wcreat"
  - "_wcreat"
  - "_creat"
  - "tcreat"
  - "_tcreat"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcreat 函数"
  - "_wcreat 函数"
  - "文件 [C++]，创建"
  - "_creat 函数"
  - "tcreat 函数"
  - "creat 函数"
  - "_tcreat 函数"
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _creat、_wcreat
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

新建文件。  `_creat` 和 `_wcreat` 已弃用；请使用 [\_sopen\_s、\_wsopen\_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md)。  
  
## 语法  
  
```  
int _creat(   
   const char *filename,  
   int pmode   
);  
int _wcreat(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### 参数  
 `filename`  
 新文件的名称。  
  
 `pmode`  
 权限设置  
  
## 返回值  
 如果成功，这些函数返回创建的文件的文件描述符。  否则，如下表所示，函数返回 \-1 并设置 `errno`。  
  
|`errno` 设置|说明|  
|----------------|--------|  
|`EACCES`|`filename` 指定现有只读文件或指定目录而不是文件。|  
|`EMFILE`|没有其他文件说明符可用。|  
|`ENOENT`|不能找到指定的文件。|  
  
 如果 `filename` 为NULL, 则函数调用无效参数处理程序, 如[参数验证](../../c-runtime-library/parameter-validation.md) 所述.  如果允许执行继续，则这些功能将 `EINVAL` 设置为 `errno` 并返回 \-1。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_creat` 函数创建新文件，或打开并截断现有的文件。  `_wcreat` 是 `_creat` 的宽字符版本；`_wcreat` 的 `filename` 参数是宽字符字符串。  `_wcreat` 和 `_creat` 行为相同，否则。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcreat`|`_creat`|`_creat`|`_wcreat`|  
  
 如果 `filename` 指定的文件不存在，则创建具有特定权限设置的新文件，并打开文件以便编写。  如果该文件已经存在，并且设置其权限为允许写入， `_creat` 文件截断为长度为 0，破坏以前内容，并打开以便编写。  权限设置，`pmode`，仅应用于新创建的文件。  在首次关闭后，新文件接收指定的权限设置。  整数表达式 `pmode` 包含SYS \\Stat.h中定义的一个或全部清单常数：`_S_IWRITE` and `_S_IREAD`。  当给定两个常数，则用按位或运算符`OR`联接   **&#124;**\).  在这种情况下，`pmode` 参数被设置为下列值之一。  
  
|值|定义|  
|-------|--------|  
|`_S_IWRITE`|允许写。|  
|`_S_IREAD`|允许读取。|  
|`_S_IREAD &#124; _S_IWRITE`|允许读取和写入。|  
  
 如果不授予写权限，此文件是只读的。  所有文件始终可读的；生成只写权限是不可能的。  模式`| _S_IWRITE` 和`_S_IWRITE``_S_IREAD`是等效的。  使用 `_creat`打开的文件,始终在`_SH_DENYNO`兼容模式中打开\(参见 [\_sopen](../../c-runtime-library/reference/sopen-wsopen.md)\) 。  
  
 `_creat`在权限设置权限之前，对`pmode`应用当前文件权限掩码\(参见 [\_umask](../../c-runtime-library/reference/umask.md)\)。  `_creat` 主要是为了与以前的库兼容。  在 `oflag` 参数中，以`_O_CREAT` 和 `_O_TRUNC`为值调用`_open`，等效于 `_creat` 且新代码倾向于前者。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_creat`|\<io.h\>|\<io.h\>, \<sys\/stat.h\>, \<sys\/types.h\>|  
|`_wcreat`|\<io.h\> or \<wchar.h\>|\<io.h\>, \<sys\/stat.h\>, \<sys\/types.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_creat.c  
// compile with: /W3  
// This program uses _creat to create  
// the file (or truncate the existing file)  
// named data and open it for writing.  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int fh;  
  
   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996  
   // Note: _creat is deprecated; use _sopen_s instead  
   if( fh == -1 )  
      perror( "Couldn't create data file" );  
   else  
   {  
      printf( "Created data file.\n" );  
      _close( fh );  
   }  
}  
```  
  
  **创建的数据文件。**   
## 请参阅  
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_dup、\_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_sopen、\_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [\_umask](../../c-runtime-library/reference/umask.md)