---
title: "_access、_waccess | Microsoft Docs"
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
  - "_access"
  - "_waccess"
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
  - "_waccess"
  - "_access"
  - "taccess"
  - "waccess"
  - "_taccess"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_access 函数"
  - "_taccess 函数"
  - "_waccess 函数"
  - "access 函数"
  - "taccess 函数"
  - "waccess 函数"
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
caps.latest.revision: 27
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _access、_waccess
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定文件是否为只读的。  更多安全版本可用；请参见 [\_access\_s、\_waccess\_s](../../c-runtime-library/reference/access-s-waccess-s.md)。  
  
## 语法  
  
```  
int _access(   
   const char *path,   
   int mode   
);  
int _waccess(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### 参数  
 `path`  
 文件或目录路径。  
  
 `mode`  
 读\/写特性。  
  
## 返回值  
 如果文件包含特定模式，每个函数返回 0。  函数返回 \- 1，则名称文件不存在或不具有特定模式；在这种情况下，如下表`errno` 所示设置。  
  
 `EACCES`  
 访问被拒绝：文件权限的设置不允许指定的访问权限。  
  
 `ENOENT`  
 未找到文件名或路径。  
  
 `EINVAL`  
 无效参数。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 当使用文件，`_access` 函数确定指定的文件或目录是否存在并且具有指定值的特性 `mode`。  在使用与目录，`_access` 确定指定的目录是否存在；只有在 [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] 和更高版本的操作系统上，所有目录读取和写入权限。  
  
|`mode` 值|检查文件。|  
|--------------|-----------|  
|00|仅存在|  
|02|Write\-only|  
|04|只读|  
|06|读取和写入|  
  
 此函数只检查是否文件和目录是只读的，则不检查文件系统安全设置。  这对于需要访问标记。  有关文件系统安全性的更多信息，请参见 [访问标记](http://msdn.microsoft.com/library/windows/desktop/aa374909)。  ATL 类存在用于提供此功能；参见 [CAccessToken Class](../../atl/reference/caccesstoken-class.md)。  
  
 `_waccess` 是 `_access` 的宽字符版本；`_waccess` 的 `path` 参数是宽字符字符串。  `_waccess` 和 `_access` 行为相同，否则。  
  
 此函数验证其参数。  如果 `path` 为 `NULL` 或 `mode` 不指定有效的模式，无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL`并返回。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_taccess`|`_access`|`_access`|`_waccess`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_access`|\<io.h\>|\<errno.h\>|  
|`_waccess`|\<wchar.h\> or \<io.h\>|\<errno.h\>|  
  
## 示例  
 下面的示例使用 `_access` 检查名为 crt\_ACCESS.C 的文件以了解其是否存在，并编写是否允许。  
  
```  
// crt_access.c  
// compile with: /W1  
// This example uses _access to check the file named  
// crt_ACCESS.C to see if it exists and if writing is allowed.  
  
#include  <io.h>  
#include  <stdio.h>  
#include  <stdlib.h>  
  
int main( void )  
{  
    // Check for existence.  
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )  
    {  
        printf_s( "File crt_ACCESS.C exists.\n" );  
  
        // Check for write permission.  
        // Assume file is read-only.  
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )  
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );  
    }  
}  
```  
  
  **文件 crt\_ACCESS.C 存在。**  
**文件 crt\_ACCESS.C 没有写权限。**   
## .NET Framework 等效项  
 <xref:System.IO.FileAccess?displayProperty=fullName>  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat、\_wstat 函数](../../c-runtime-library/reference/stat-functions.md)