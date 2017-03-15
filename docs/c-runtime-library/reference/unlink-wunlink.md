---
title: "_unlink、_wunlink | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_unlink"
  - "_wunlink"
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
  - "_tunlink"
  - "_unlink"
  - "wunlink"
  - "_wunlink"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tunlink 函数"
  - "_unlink 函数"
  - "_wunlink 函数"
  - "文件 [C++], 删除"
  - "文件 [C++], 移除"
  - "tunlink 函数"
  - "unlink 函数"
  - "wunlink 函数"
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _unlink、_wunlink
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

删除文件。  
  
## 语法  
  
```  
int _unlink(  
   const char *filename   
);  
int _wunlink(  
   const wchar_t *filename   
);  
```  
  
#### 参数  
 `filename`  
 移除文件名。  
  
## 返回值  
 如果成功，这些函数中的每个表达式都返回 0。  否则，函数返回 \- 1 并将 `errno` 设置为 `EACCES`，则意味着路径指定只读文件，或为 `ENOENT`，这意味着文件未找到或路径指定的目录未找到。  
  
 有关这些内容的详细信息以及其他返回代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_unlink` 函数删除通过`filename` 指定的文件。  `_wunlink` 是 `_unlink` 的宽字符版本；`_wunlink` 的 `filename` 参数是宽字符字符串。  否则这些函数具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE  & \_MBCS 未定义|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-----------------------------|----------------|-------------------|  
|`_tunlink`|`_unlink`|`_unlink`|`_wunlink`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_unlink`|\<io.h\> and \<stdio.h\>|  
|`_wunlink`|\<io.h\> or \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 代码示例  
 本程序使用\_unlink 删除 CRT\_UNLINK.TXT。  
  
```  
// crt_unlink.c  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( _unlink( "crt_unlink.txt" ) == -1 )  
      perror( "Could not delete 'CRT_UNLINK.TXT'" );  
   else  
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );  
}  
```  
  
### Input: crt\_unlink.txt  
  
```  
This file will be deleted.  
```  
  
### 示例输出  
  
```  
Deleted 'CRT_UNLINK.TXT'  
```  
  
## .NET Framework 等效项  
 [System::IO::File::删除](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [remove、\_wremove](../../c-runtime-library/reference/remove-wremove.md)