---
title: "_set_fmode | Microsoft Docs"
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
  - "_set_fmode"
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
  - "_set_fmode"
  - "set_fmode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_fmode 函数"
  - "文件翻译 [C++], 默认模式"
  - "文件翻译 [C++], 设置模式"
  - "set_fmode 函数"
ms.assetid: f80eb9c7-733b-4652-a9bc-6b3790a35f12
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_fmode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置文件 I\/O 操作的默认文件翻译模式。  
  
## 语法  
  
```  
errno_t _set_fmode(   
   int mode   
);  
```  
  
#### 参数  
 \[in\] `mode`  
 文件所需的特定模式：`_O_TEXT` 或 `_O_BINARY`。  
  
## 返回值  
 如果成功，返回零；如果失败，则为错误代码。  如果 `mode` 不是 `_O_TEXT` 或 `_O_BINARY` 或 `_O_WTEXT`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EINVAL`。  
  
## 备注  
 函数设置 [\_fmode](../../c-runtime-library/fmode.md) 全局变量。  此变量为文件 I\/O 操作 `_open` 和 `_pipe`指定默认文件的特定转换模式。  
  
 `_O_TEXT` 和 `_O_BINARY` 在 Fcntl.h 中进行定义。  `EINVAL` 在 Errno.h 定义。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_set_fmode`|\<stdlib.h\>|\<fcntl.h，errno.h\>\<\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_set_fmode.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <fcntl.h>     /* for _O_TEXT and _O_BINARY */  
#include <errno.h>     /* for EINVAL */  
#include <sys\stat.h>  /* for _S_IWRITE */  
#include <share.h>     /* for _SH_DENYNO */  
  
int main()  
{  
   int mode, fd, ret;  
   errno_t err;  
   int buf[12] = { 65, 66, 67, 68, 69, 70, 71, 72, 73, 74,  
                   75, 76 };  
   char * filename = "fmode.out";  
  
   err = _get_fmode(&mode);  
   if (err == EINVAL)  
   {  
      printf( "Invalid parameter: mode\n");  
      return 1;  
   }  
   else  
      printf( "Default Mode is %s\n", mode == _O_TEXT ? "text" :  
              "binary");  
  
   err = _set_fmode(_O_BINARY);  
   if (err == EINVAL)  
   {  
      printf( "Invalid mode.\n");  
      return 1;  
   }  
  
   if ( _sopen_s(&fd, filename, _O_RDWR | _O_CREAT, _SH_DENYNO, _S_IWRITE | _S_IREAD) != 0 )  
   {  
      printf( "Error opening the file %s\n", filename);  
      return 1;  
   }  
  
   if (ret = _write(fd, buf, 12*sizeof(int)) < 12*sizeof(int))  
   {  
      printf( "Problem writing to the file %s.\n", filename);  
      printf( "Number of bytes written: %d\n", ret);  
   }  
  
   if (_close(fd) != 0)  
   {  
      printf("Error closing the file %s. Error code %d.\n",  
             filename, errno);  
   }  
  
   system("type fmode.out");  
}  
```  
  
  **Default Mode is binary**  
**A   B   C   D   E   F   G   H   I   J   K   L**   
## 请参阅  
 [\_fmode](../../c-runtime-library/fmode.md)   
 [\_get\_fmode](../../c-runtime-library/reference/get-fmode.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [文本和二进制模式文件 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)