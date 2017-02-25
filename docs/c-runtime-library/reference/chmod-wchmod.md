---
title: "_chmod、_wchmod | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_chmod"
  - "_wchmod"
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
  - "_chmod"
  - "_wchmod"
  - "wchmod"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_chmod 函数"
  - "_wchmod 函数"
  - "chmod 函数"
  - "文件权限 [C++]"
  - "文件 [C++], 更改权限"
  - "wchmod 函数"
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _chmod、_wchmod
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

更改文件权限设置。  
  
## 语法  
  
```  
  
      int _chmod(   
   const char *filename,  
   int pmode   
);  
int _wchmod(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### 参数  
 `filename`  
 存在文件的名称。  
  
 `pmode`  
 文件权限的设置。  
  
## 返回值  
 如果权限设置更改成功，这些函数返回 0。  返回值– 1 指示失败。  如果找不到指定的文件，`errno` 将设置为 `ENOENT`;如果参数无效，则 `errno` 设置为 `EINVAL`。  
  
## 备注  
 `filename` 函数改变由指 `_chmod` 指定的文件权限设置*。*权限控制设置控制文件的读写访问。  整数表达式 `pmode` 包含以下 SYS\\STAT.H定义中的一个或全部清单常数：  
  
 `_S_IWRITE`  
 允许写。  
  
 `_S_IREAD`  
 允许读取。  
  
 `_S_IREAD | _S_IWRITE`  
 允许读取和写入。  
  
 当给定两个常数，则用按位或运算符`OR`联接          `|` \).  如果不授予写权限，此文件是只读的。  注意所有文件始终可读的；生成只写权限是不可能的。  因此，`_S_IWRITE` 和 `_S_IREAD | _S_IWRITE` 是等效的。  
  
 `_wchmod` 是 `_chmod` 的宽字符版本；`_wchmod` 的 `filename` 参数是宽字符字符串。  `_wchmod` 和 `_chmod` 行为相同，否则。  
  
 此函数验证其参数。  如果 `pmode` 不是组合的清单常数也没有并入重写项组常量，函数将会忽略这些。  如果 `filename` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回\-1。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tchmod`|`_chmod`|`_chmod`|`_wchmod`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_chmod`|\<io.h\>|\<io.h\>, \<sys\/stat.h\>, \<sys\/types.h\>|  
|`_wchmod`|\<io.h\> or \<wchar.h\>|\<io.h\>, \<sys\/stat.h\>, \<sys\/types.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_chmod.c  
// This program uses _chmod to  
// change the mode of a file to read-only.  
// It then attempts to modify the file.  
//  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
// Change the mode and report error or success   
void set_mode_and_report(char * filename, int mask)  
{  
   // Check for failure   
   if( _chmod( filename, mask ) == -1 )  
   {  
      // Determine cause of failure and report.   
      switch (errno)  
      {  
         case EINVAL:  
            fprintf( stderr, "Invalid parameter to chmod.\n");  
            break;  
         case ENOENT:  
            fprintf( stderr, "File %s not found\n", filename );  
            break;  
         default:  
            // Should never be reached   
            fprintf( stderr, "Unexpected error in chmod.\n" );  
       }  
   }  
   else  
   {  
      if (mask == _S_IREAD)  
        printf( "Mode set to read-only\n" );  
      else if (mask & _S_IWRITE)  
        printf( "Mode set to read/write\n" );  
   }  
   fflush(stderr);  
}  
  
int main( void )  
{   
  
   // Create or append to a file.   
   system( "echo /* End of file */ >> crt_chmod.c_input" );  
  
   // Set file mode to read-only:   
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );  
  
   system( "echo /* End of file */ >> crt_chmod.c_input " );  
  
   // Change back to read/write:   
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );  
  
   system( "echo /* End of file */ >> crt_chmod.c_input " );   
}   
```  
  
  **`行文本。` `行文本。`模式设置为只读的**  
**拒绝访问。**  
**模式设置为可读\/可写**   
## .NET Framework 等效项  
  
-   [System.IO.File::GetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)  
  
-   [System::Security::Permissions::FileIOPermission](https://msdn.microsoft.com/en-us/library/system.security.permissions.fileiopermission.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat、\_wstat 函数](../../c-runtime-library/reference/stat-functions.md)