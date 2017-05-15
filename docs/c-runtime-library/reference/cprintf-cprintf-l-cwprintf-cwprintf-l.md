---
title: "_cprintf、_cprintf_l、_cwprintf、_cwprintf_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cwprintf_l
- _cprintf_l
- _cwprintf
- _cprintf
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
apitype: DLLExport
f1_keywords:
- _cwprintf
- cwprintf
- tcprintf
- _tcprintf
- _cprintf
- cwprintf_l
- tcprintf_l
- _tcprintf_l
- cprintf_l
- _cprintf_l
- _cwprintf_l
dev_langs:
- C++
helpviewer_keywords:
- _cprintf_l function
- _cwprintf_l function
- cwprintf function
- cprintf_l function
- characters, printing to console
- printing characters to console
- _tcprintf_l function
- tcprintf function
- _tcprintf function
- tcprintf_l function
- _cwprintf function
- cwprintf_l function
- _cprintf function
ms.assetid: 67ffefd4-45b3-4be0-9833-d8d26ac7c4e2
caps.latest.revision: 34
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
ms.openlocfilehash: c96743fc777a53f2fe849d5f88f3fd7299054d02
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="cprintf-cprintfl-cwprintf-cwprintfl"></a>_cprintf、_cprintf_l、_cwprintf、_cwprintf_l
格式化并打印到控制台。 提供更为安全的版本；请参阅 [_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _cprintf(   
   const char * format [, argument_list]  
);  
int _cprintf_l(  
   const char * format,  
   locale_t locale [, argument_list]  
);  
int _cwprintf(  
   const wchar * format [, argument_list]  
);  
int _cwprintf_l(  
   const wchar * format,  
   locale_t locale [, argument_list]  
);  
```  
  
#### <a name="parameters"></a>参数  
 `format`  
 窗体控件字符串。  
  
 `argument_list`  
 格式字符串的可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 打印的字符数。  
  
## <a name="remarks"></a>备注  
 这些函数会格式化一系列字符和值并将其直接输出到控制台，并使用 `_putch` 函数（`_cwprintf` 为 `_putwch`）来输出字符。 在每个自变量`argument_list`（如果有） 进行转换和输出中的相应格式规范根据`format`。 `format`自变量使用[格式规范语法 printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。 与不同`fprintf`， `printf`，和`sprintf`函数，两者`_cprintf`也不`_cwprintf`会换行字符将转换为回车换行符 (CR-LF) 组合输出时。  
  
 一个重要区别在于，`_cwprintf`显示 Unicode 字符在 Windows 中使用时。 与 `_cprintf` 不同，`_cwprintf` 使用当前控制台区域设置。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  
  
 `_cprintf` 验证 `format` 参数。 如果 `format` 为空指针，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回 -1 并将 `errno` 设置为 `EINVAL`。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcprintf`|`_cprintf`|`_cprintf`|`_cwprintf`|  
|`_tcprintf_l`|`_cprintf_l`|`_cprintf_l`|`_cwprintf_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_cprintf`，`_cprintf_l`|\<conio.h>|  
|`_cwprintf`, `_cwprintf_l`|\<conio.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_cprintf.c  
// compile with: /c  
// This program displays some variables to the console.  
  
#include <conio.h>  
  
int main( void )  
{  
    int         i = -16,  
                h = 29;  
    unsigned    u = 62511;  
    char        c = 'A';  
    char        s[] = "Test";  
  
    // Note that console output does not translate \n as  
    // standard output does. Use \r\n instead.  
    //  
    _cprintf( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );  
}  
```  
  
```Output  
-16  001d  62511  A Test  
```  
  
## <a name="see-also"></a>另请参阅  
 [控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)   
 [_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)   
 [_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)
