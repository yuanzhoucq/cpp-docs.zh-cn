---
title: "remove、_wremove | Microsoft Docs"
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
  - "_wremove"
  - "remove"
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
  - "remove"
  - "_wremove"
  - "_tremove"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tremove 函数"
  - "_wremove 函数"
  - "文件 [C++], 删除"
  - "文件 [C++], 移除"
  - "remove 函数"
  - "tremove 函数"
  - "wremove 函数"
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remove、_wremove
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

删除文件。  
  
## 语法  
  
```  
  
      int remove(  
   const char *path   
);  
int _wremove(  
   const wchar_t *path   
);  
```  
  
#### 参数  
 *path*  
 要移除的文件路径。  
  
## 返回值  
 如果目录成功被删除，则这些函数返回0。  否则，返回 \-1 并将 `errno` 设置为 `EACCES` 以指示任何路径指定只读文件打开，或对指示 **ENOENT** 文件名或未找到路径或路径指定目录。  
  
 有关这些内容的详细信息以及其他返回代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 **remove** 函数删除 *路径指定的文件。* `_wremove` 是 **\_remove** 的是宽字符版本；*path* 的参数 `_wremove` 是字符串。  除此以外，`_wremove` 和 **\_remove** 的行为完全相同。  对文件的任意图柄必须在删除之前关闭。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS not defined|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------------|----------------|-------------------|  
|`_tremove`|**remove**|**remove**|`_wremove`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**remove**|\<stdio.h\> or \<io.h\>|  
|`_wremove`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_remove.c  
/* This program uses remove to delete crt_remove.txt */  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( remove( "crt_remove.txt" ) == -1 )  
      perror( "Could not delete 'CRT_REMOVE.TXT'" );  
   else  
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );  
}  
```  
  
## Input: crt\_remove.txt  
  
```  
This file will be deleted.  
```  
  
## 示例输出  
  
```  
Deleted 'CRT_REMOVE.TXT'  
```  
  
## .NET Framework 等效项  
 [System::IO::File::删除](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_unlink、\_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)