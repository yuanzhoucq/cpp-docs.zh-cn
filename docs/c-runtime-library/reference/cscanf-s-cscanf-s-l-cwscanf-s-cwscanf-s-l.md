---
title: "_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cwscanf_s_l
- _cwscanf_s
- _cscanf_s
- _cscanf_s_l
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
- cscanf_s
- cscanf_s_l
- cwscanf_s
- _cwscanf_s
- _tcscanf_s
- _cscanf_s
- _cwscanf_s_l
- _cscanf_s_l
- cwscanf_s_l
- _tcscanf_s_l
- tcscanf_s
- tcscanf_s_l
dev_langs: C++
helpviewer_keywords:
- cscanf_s function
- _cwscanf_s_l function
- tcscanf_s function
- console [C++], reading from
- _cscanf_s function
- data [C++], reading from the console
- cwscanf_s function
- _tcscanf_s_l function
- _cscanf_s_l function
- cscanf_s_l function
- cwscanf_s_l function
- reading data [C++], from the console
- _cwscanf_s function
- _tcscanf_s function
- tcscanf_s_l function
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cf20837a7abc336f120f031636a67264549e8d11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cscanfs-cscanfsl-cwscanfs-cwscanfsl"></a>_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l
从控制台读取格式数据。 这些更安全版本的 [_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _cscanf_s(   
   const char *format [,  
   argument] ...   
);  
int _cscanf_s_l(   
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _cwscanf_s(   
   const wchar_t *format [,  
   argument] ...   
);  
int _cwscanf_s_l(   
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
```  
  
#### <a name="parameters"></a>参数  
 `format`  
 窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 已成功转换和分配的字段数。 返回值不包括已读取但未分配的字段。 返回值为尝试在文件结尾读取的 `EOF`。 在操作系统命令行级别重定向键盘输入时，会发生这种情况。 返回值为 0 表示没有分配任何字段。  
  
 这些函数验证其参数。 如果 `format` 为空指针，则这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回`EOF`和`errno`设置为`EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_cscanf_s` 函数直接将数据从控制台读取到 `argument` 给定的位置。 [_Getche](../../c-runtime-library/reference/getch-getwch.md) 函数用于读取字符。 每个可选参数都必须为指向类型的变量的指针，该类型与 `format` 中的类型说明符对应。 格式控制输入字段的解释，格式和函数与 [scanf_s](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函数的 `format` 参数相同。 虽然 `_cscanf_s` 通常回显输入字符，但如果最后一次调用的是 `_ungetch`，则不会执行此操作。  
  
 像其他安全版本中的函数的`scanf`系列，`_cscanf_s`和`_cswscanf_s`需要类型字段字符的大小参数`c`， `C`， `s`， `S`，和`[`。 有关详细信息，请参阅 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。  
  
> [!NOTE]
>  大小参数的类型具有 `unsigned`，而不具有 `size_t`。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcscanf_s`|`_cscanf_s`|`_cscanf_s`|`_cwscanf_s`|  
|`_tcscanf_s_l`|`_cscanf_s_l`|`_cscanf_s_l`|`_cwscanf_s_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_cscanf_s`，`_cscanf_s_l`|\<conio.h>|  
|`_cwscanf_s`, `_cwscanf_s_l`|\<conio.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_cscanf_s.c  
// compile with: /c  
/* This program prompts for a string  
 * and uses _cscanf_s to read in the response.  
 * Then _cscanf_s returns the number of items  
 * matched, and the program displays that number.  
 */  
  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int result, n[3];  
   int i;  
  
   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );  
   _cprintf_s( "\r\nYou entered " );  
   for( i=0; i<result; i++ )  
      _cprintf_s( "%i ", n[i] );  
   _cprintf_s( "\r\n" );  
}  
```  
  
## <a name="input"></a>输入  
  
```  
1 2 3  
```  
  
## <a name="output"></a>输出  
  
```  
You entered 1 2 3  
```  
  
## <a name="see-also"></a>另请参阅  
 [控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)   
 [_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)   
 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)