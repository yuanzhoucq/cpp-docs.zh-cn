---
title: "_access_s、_waccess_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_access_s"
  - "_waccess_s"
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
  - "waccess_s"
  - "access_s"
  - "_waccess_s"
  - "_access_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_access_s 函数"
  - "_taccess_s 函数"
  - "_waccess_s 函数"
  - "access_s 函数"
  - "taccess_s 函数"
  - "waccess_s 函数"
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# _access_s、_waccess_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定文件读取\/写入访问权限。  [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t _access_s(   
   const char *path,   
   int mode   
);  
errno_t _waccess_s(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### 参数  
 `path`  
 文件或目录路径。  
  
 `mode`  
 权限设置  
  
## 返回值  
 如果文件包含特定模式，每个函数返回 0。  函数返回了错误代码，则在特定的模式，命名的文件不存在或无法访问。  在这种情况下，函数集合返回代码错误并将 `errno` 设置为相同的值。  
  
 `EACCES`  
 访问被拒绝。  文件权限的设置不允许指定的访问权限。  
  
 `ENOENT`  
 未找到文件名或路径。  
  
 `EINVAL`  
 无效参数。  
  
 有关更多信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 当使用文件时，`_access_s` 函数来确定指定的文件是否存在并且可以根据 `mode`值访问。  在使用目录时，`_access_s` 只确定指定的目录是否存在。  在 [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] 和更高版本的操作系统上，所有目录有读取和写入权限。  
  
|模式值|检查文件。|  
|---------|-----------|  
|00|仅存在。|  
|02|写入权限。|  
|04|读权限。|  
|06|读取和写入许可。|  
  
 读取或写入文件的权限不足够确保能打开文件。  例如，如果文件被另一进程锁定，它可能不可访问，即使 `_access_s` 返回 0。  
  
 `_waccess_s` 是 `_access_s` 的宽字符版本；`_waccess_s` 的 `path` 参数是宽字符字符串。  除此以外，`_waccess_s` 和 `_access_s` 的行为完全相同。  
  
 这些函数验证其参数。  如果 `path` 为 `NULL` 或 `mode` 不指定有效的模式，无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回`EINVAL`。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_taccess_s`|`_access_s`|`_access_s`|`_waccess_s`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_access_s`|\<io.h\>|\<errno.h\>|  
|`_waccess_s`|\<wchar.h\> or \<io.h\>|\<errno.h\>|  
  
## 示例  
 示例使用 `_access_s` 检查名为 crt\_access\_s.c 的文件以了解其是否存在，并编写是否允许。  
  
```  
// crt_access_s.c  
  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    errno_t err = 0;  
  
    // Check for existence.   
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )  
    {  
        printf_s( "File crt_access_s.c exists.\n" );  
  
        // Check for write permission.   
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )  
        {  
            printf_s( "File crt_access_s.c does have "  
                      "write permission.\n" );  
        }  
        else  
        {  
            printf_s( "File crt_access_s.c does not have "  
                      "write permission.\n" );  
        }  
    }  
    else  
    {  
        printf_s( "File crt_access_s.c does not exist.\n" );  
    }  
}  
```  
  
  **文件 crt\_access\_s.c 存在。**  
**文件 crt\_access\_s.c 没有写权限。**   
## .NET Framework 等效项  
 <xref:System.IO.FileAccess?displayProperty=fullName>  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat、\_wstat 函数](../../c-runtime-library/reference/stat-functions.md)