---
title: "_access、_waccess | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _access
- _waccess
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _waccess
- _access
- taccess
- waccess
- _taccess
dev_langs:
- C++
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: d0968ec14a43cfbbf1169f34ac929435787bc349
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="access-waccess"></a>_access、_waccess
确定文件是否是只读的。 提供更多的安全版本；请参阅 [_access_s、_waccess_s](../../c-runtime-library/reference/access-s-waccess-s.md)。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `path`  
 文件或目录路径。  
  
 `mode`  
 读取/写入属性。  
  
## <a name="return-value"></a>返回值  
 如果该文件具有给定的模式，则每个函数将返回 0。 如果已命名的文件不存在或不具有给定的模式;，函数将返回-1在这种情况下，`errno`下表中所示设置。  
  
 `EACCES`  
 拒绝访问：文件的权限设置不允许指定的访问权限。  
  
 `ENOENT`  
 未找到文件名或路径。  
  
 `EINVAL`  
 参数无效。  
  
 有关这些代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 与文件一起使用时，`_access` 函数确定指定的文件或目录是否存在，并且是否具有由 `mode` 值指定的属性。 与目录一起使用时，`_access` 仅确定指定的目录是否存在；在 [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] 和更高版本的操作系统中，所有目录都具有读取和写入访问权限。  
  
|`mode` 值|文件检查内容|  
|------------------|---------------------|  
|00|仅检查是否存在|  
|02|只写|  
|04|只读|  
|06|读取和写入|  
  
 此函数仅检查文件和目录是否为只读，不检查文件系统安全设置。 因此，你需要访问令牌。 有关文件系统安全性的详细信息，请参阅[访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)。 存在 ATL 类以提供此功能；请参阅 [CAccessToken 类](../../atl/reference/caccesstoken-class.md)。  
  
 `_waccess` 是 `_access` 的宽字符版本；`path` 的 `_waccess` 参数是宽字符字符串。 除此以外，`_waccess` 和 `_access` 的行为完全相同。  
  
 此函数验证其参数。 如果 `path` 为 `NULL` 或 `mode` 未指定有效模式，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则该函数将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_taccess`|`_access`|`_access`|`_waccess`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|----------------------|  
|`_access`|\<io.h>|\<errno.h>|  
|`_waccess`|\<wchar.h> 或 \<io.h>|\<errno.h>|  
  
## <a name="example"></a>示例  
 以下示例使用 `_access` 检查名为 crt_ACCESS.C 的文件，以查看其是否存在以及是否允许写入。  
  
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
  
```Output  
File crt_ACCESS.C exists.  
File crt_ACCESS.C does not have write permission.  
```  
  
## <a name="see-also"></a>另请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_stat、_wstat 函数](../../c-runtime-library/reference/stat-functions.md)
