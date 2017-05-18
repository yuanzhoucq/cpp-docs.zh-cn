---
title: "getenv、_wgetenv | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getenv
- _wgetenv
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
- _wgetenv
- getenv
- _tgetenv
dev_langs:
- C++
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
caps.latest.revision: 31
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 2838a1c79ad97bfd665a367b2a597cb20ac70097
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="getenv-wgetenv"></a>getenv、_wgetenv
从当前环境中获取值。 提供这些函数的更安全版本；请参阅 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
char *getenv(   
   const char *varname   
);  
wchar_t *_wgetenv(   
   const wchar_t *varname   
);  
```  
  
#### <a name="parameters"></a>参数  
 `varname`  
 环境变量名称。  
  
## <a name="return-value"></a>返回值  
 返回指向包含 `varname` 的环境表项的指针。 使用返回的指针修改环境变量并不安全。 请使用 `_putenv` 函数修改环境变量的值。 如果在环境表中找不到 `varname`，则返回值为 `NULL`。  
  
## <a name="remarks"></a>备注  
 `getenv` 函数将搜索 `varname` 的环境变量列表。 在 Windows 操作系统中，`getenv` 不区分大小写。 `getenv` 和 `_putenv` 使用全局变量 `_environ` 所指向环境的副本来访问该环境。 `getenv` 只能在可访问运行时库的数据结构上执行，不能在由操作系统对进程创建的环境“段”上执行。 因此，对 [main](../../cpp/main-program-startup.md) 或 [wmain](../../cpp/main-program-startup.md) 使用 `envp` 参数的程序可能会检索无效信息。  
  
 如果 `varname` 是 `NULL`，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `NULL`。  
  
 `_wgetenv` 是 `getenv` 的宽字符版本；`_wgetenv` 的参数和返回值都是宽字符字符串。 `_wenviron` 全局变量是 `_environ` 的宽字符版本。  
  
 在 MBCS 程序中（例如，在 SBCS ASCII 程序中），`_wenviron` 最初为 `NULL`，因为环境是由多字节字符字符串组成的。 然后，在首次调用 `_wputenv` 或首次调用 `_wgetenv` 时，如果 (MBCS) 环境已存在，则将由 `_wenviron` 创建对应的宽字符字符串环境并指向该环境。  
  
 同样，在 Unicode (`_wmain`) 程序中，`_environ` 最初为 `NULL`，因为环境是由宽字符字符串组成的。 然后，在首次调用 `_putenv` 或在首次调用 `getenv` 时，如果 (Unicode) 环境已存在，则将由 `_environ` 创建对应的 MBCS 环境并指向该环境。  
  
 当程序中同时存在环境的两个副本（MBCS 和 Unicode）时，运行时系统必须保留这两个副本，而这将减慢执行时间。 例如，当调用 `_putenv` 时，也会自动调用 `_wputenv`，以便两个环境字符串相对应。  
  
> [!CAUTION]
>  在极少数情况下，当运行时系统同时保留环境的 Unicode 版本和多字节版本时，两个环境版本可能不完全对应。 这是因为，虽然任何唯一的多字节字符字符串将映射到唯一的 Unicode 字符串，但从唯一的 Unicode 字符串到多字节字符字符串的映射却不一定是唯一的。 有关详细信息，请参阅 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv` 和 `_getenv` 系列的函数不是线程安全函数。 当 `_putenv` 修改字符串时，`_getenv` 可能会返回字符串指针，从而导致随机性失败。 确保对这些函数的调用同步。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tgetenv`|`getenv`|`getenv`|`_wgetenv`|  
  
 若要检查或更改 `TZ` 环境变量的值，请按需使用 `getenv`、`_putenv` 和 `_tzset`。 有关 `TZ` 的详细信息，请参阅 [_tzset](../../c-runtime-library/reference/tzset.md) 以及 [_daylight、timezone 和 _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`getenv`|\<stdlib.h>|  
|`_wgetenv`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_getenv.c  
// compile with: /W3  
// This program uses getenv to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *libvar;  
  
   // Get the value of the LIB environment variable.  
   libvar = getenv( "LIB" ); // C4996  
   // Note: getenv is deprecated; consider using getenv_s instead  
  
   if( libvar != NULL )  
      printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects the environment  
   // variable of the current process. The command processor's  
   // environment is not changed.  
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996  
   // Note: _putenv is deprecated; consider using putenv_s instead  
  
   // Get new value.  
   libvar = getenv( "LIB" ); // C4996  
  
   if( libvar != NULL )  
      printf( "New LIB variable is: %s\n", libvar );  
}  
```  
  
```Output  
Original LIB variable is: C:\progra~1\devstu~1\vc\lib  
New LIB variable is: c:\mylib;c:\yourlib  
```  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_putenv、_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [环境常量](../../c-runtime-library/environmental-constants.md)
