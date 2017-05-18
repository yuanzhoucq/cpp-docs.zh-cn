---
title: "_searchenv、_wsearchenv | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _searchenv
- _wsearchenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
dev_langs:
- C++
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
caps.latest.revision: 33
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
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: 2c71b97e925ab23c893eefd6092efffe57bea3a7
ms.contentlocale: zh-cn
ms.lasthandoff: 02/28/2017

---
# <a name="searchenv-wsearchenv"></a>_searchenv、_wsearchenv
使用环境路径搜索文件。 提供这些函数的更多安全版本；请参阅 [_searchenv_s、_wsearchenv_s](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
void _searchenv(  
   const char *filename,  
   const char *varname,  
   char *pathname   
);  
void _wsearchenv(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t *pathname   
);  
template <size_t size>  
void _searchenv(  
   const char *filename,  
   const char *varname,  
   char (&pathname)[size]  
); // C++ only  
template <size_t size>  
void _wsearchenv(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t (&pathname)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `filename`  
 要搜索的文件名称。  
  
 `varname`  
 要搜索的环境。  
  
 `pathname`  
 用于存储完整路径的缓冲区。  
  
## <a name="remarks"></a>备注  
 `_searchenv` 例程搜索指定域中的目标文件。 `varname` 变量可以是指定目录路径的列表的任何环境或用户定义的变量（例如，`PATH`、`LIB` 或 `INCLUDE`）。 由于 `_searchenv` 区分大小写，因此 `varname` 应与环境变量的情况匹配。  
  
 例程首先搜索当前工作目录中的文件。 如果找不到文件，它将查找由环境变量指定的目录。 如果目标文件在其中一个目录中，则新创建的路径将被复制到 `pathname` 中。 如果找不到 `filename` 文件，`pathname` 将包含一个以 null 值结束的空字符串。  
  
 `pathname` 缓冲区的字符长度至少应为 `_MAX_PATH`，以便容纳构建的路径名称的完整长度。 否则，`_searchenv` 可能溢出 `pathname` 缓冲并导致意外行为。  
  
 `_wsearchenv` 是 `_searchenv` 的宽字符版本，并且 `_wsearchenv` 的参数是宽字符字符串。 除此以外，`_wsearchenv` 和 `_searchenv` 的行为完全相同。  
  
 如果 `filename` 为空字符串，这些函数将返回 `ENOENT`。  
  
 如果 `filename` 或 `pathname` 是 `NULL` 指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则这些函数返回 -1 并将 `errno` 设置为 `EINVAL`。  
  
 有关 `errno` 和错误代码的详细信息，请参阅 [errno 常量](../../c-runtime-library/errno-constants.md)。  
  
 在 C++ 中，这些函数具有可调用这些函数的更新、更安全的版本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv`|`_searchenv`|`_searchenv`|`_wsearchenv`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_searchenv`|\<stdlib.h>|  
|`_wsearchenv`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```C  
// crt_searchenv.c  
// compile with: /W3  
// This program searches for a file in  
// a directory that's specified by an environment variable.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char pathbuffer[_MAX_PATH];  
   char searchfile[] = "CL.EXE";  
   char envvar[] = "PATH";  
  
   // Search for file in PATH environment variable:  
   _searchenv( searchfile, envvar, pathbuffer ); // C4996  
   // Note: _searchenv is deprecated; consider using _searchenv_s  
   if( *pathbuffer != '\0' )  
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );  
   else  
      printf( "%s not found\n", searchfile );  
}  
```  
  
```Output  
Path for CL.EXE:  
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE  
```  
  
## <a name="see-also"></a>另请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [getenv、_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv、_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [_searchenv_s、_wsearchenv_s](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)
