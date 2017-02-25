---
title: "_futime、_futime32、_futime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_futime64"
  - "_futime32"
  - "_futime"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "futime"
  - "_futime"
  - "futime64"
  - "_futime64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_futime 函数"
  - "futime32 函数"
  - "futime64 函数"
  - "文件修改时间 [C++]"
  - "_futime64 函数"
  - "futime 函数"
  - "_futime32 函数"
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _futime、_futime32、_futime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

修改打开文件的时间。  
  
## 语法  
  
```  
int _futime(   
   int fd,  
   struct _utimbuf *filetime   
);  
int _futime32(   
   int fd,  
   struct __utimbuf32 *filetime   
);  
int _futime64(   
   int fd,  
   struct __utimbuf64 *filetime   
);  
```  
  
#### 参数  
 `fd`  
 引用开启文件的描述符。  
  
 `filetime`  
 为包含的新日期修改结构的指针。  
  
## 返回值  
 如果成功，则返回0。  如果错误发生，则将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果实现允许继续，返回函数 \- 1 与 `errno` 设置为 `EBADF`，则指示无效的文件说明符或 `EINVAL`，指示的参数无效。  
  
## 备注  
 `_futime` 例程设置修改访问日期和时间在打开文件与 `fd`*。* `_futime` 与 [\_utime](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)相同，只不过其参数是，打开的文件文件说明符，而不是路径或文件的名称写入文件。  `_utimbuf` 结构包含新的修改日期和访问时间字段。  两个字段必须包含有效值。  `_utimbuf32` 和 `_utimbuf64` 与 `_utimbuf` 是相同的 \(分别使用 32 位、64 位时间类型）。  `_futime` 和 `_utimbuf` 使用 64 位时类型，并且 `_futime` 在与 `_futime64`的行为相同。  如果需要强制旧行为，请定义 `_USE_32BIT_TIME_T`。  这样做使 `_futime` 相同中行为的 `_futime32` 并使 `_utimbuf` 结构使用 32 位时类型，使其等效于 `__utimbuf32`。  
  
 `_futime64`，使用 `__utimbuf64` 结构可以通过读取和修改文件日期3000 年 12 月 31 日23:59:59，UTC;然而对 `_futime32` 的调用失败，则文件上的日期晚于2038 年1 月 18 日19:14:07，UTC。  1970 年 1 月 1 日 00:00:00，是这些函数的下限的日期范围。  
  
## 要求  
  
|功能|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_futime`|\<sys\/utime.h\>|\<errno.h\>|  
|`_futime32`|\<sys\/utime.h\>|\<errno.h\>|  
|`_futime64`|\<sys\/utime.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_futime.c  
// This program uses _futime to set the  
// file-modification time to the current time.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <io.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/utime.h>  
#include <share.h>  
  
int main( void )  
{  
   int hFile;  
  
   // Show file time before and after.   
   system( "dir crt_futime.c_input" );  
  
   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );  
  
   if( _futime( hFile, NULL ) == -1 )  
      perror( "_futime failed\n" );  
   else  
      printf( "File time modified\n" );  
  
   _close (hFile);  
  
   system( "dir crt_futime.c_input" );  
}  
```  
  
## Input: crt\_futime.c\_input  
  
```  
Arbitrary file contents.  
```  
  
### 示例输出  
  
```  
Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:40 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
 Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:41 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
File time modified  
```  
  
## .NET Framework 等效项  
  
-   [System::IO::File::SetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastaccesstime.aspx)  
  
-   [System::IO::File::SetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastwritetime.aspx)  
  
-   [System::IO::File::SetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.setcreationtime.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)