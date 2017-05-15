---
title: "sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
dev_langs:
- C++
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 59693a41b76eb7d6d7bae4c50fa320d8f48c78d1
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="sscanfs-sscanfsl-swscanfs-swscanfsl"></a>sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l
从字符串中读取格式化数据。 这些版本的 [sscanf、_sscanf_l、swscanf、_swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md) 具有安全性增强功能，如 [CRT 的安全性增强功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## <a name="syntax"></a>语法  
  
```  
int sscanf_s(  
   const char *buffer,  
   const char *format [,  
   argument ] ...  
);  
int _sscanf_s_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...  
);  
int swscanf_s(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...  
);  
int _swscanf_s_l(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ] ...  
);  
```  
  
#### <a name="parameters"></a>参数  
 `buffer`  
 存储的数据  
  
 `format`  
 窗体控件字符串。 有关详细信息，请参阅[格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
 `argument`  
 可选自变量  
  
 `locale`  
 要使用的区域设置  
  
## <a name="return-value"></a>返回值  
 每个函数都将返回成功转换并分配的字段数；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 如果在首次转换前到达字符串的结尾，则返回值为 `EOF` 以指示错误。  
  
 如果 `buffer` 或 `format` 是 `NULL` 指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数返回 -1 并将 `errno` 设置为 `EINVAL`  
  
 有关这些及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `sscanf_s` 函数将数据从 `buffer` 读入每个 `argument` 给定的位置。 格式字符串之后的参数指定指向类型与 `format` 中的类型说明符相对应的变量的指针。 与不太安全的版本 `sscanf` 不同，使用类型字段字符 `c`、`C`、`s`、`S` 或括在 `[]` 中的字符串控件集时，需要使用缓冲区大小参数。 必须紧跟在需要缓冲区大小的缓冲区参数后提供缓冲区大小（以字符为单位）作为附加参数。 例如，如果你正在读入一个字符串，则将传递该字符串的缓冲区大小，如下所示：  
  
 `wchar_t ws[10];`  
  
 `swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9`  
  
 缓冲区大小包括终止 null 字符。 可以使用宽度规范字段来确保读入的标记可放入缓冲区中。 如果未使用任何宽度规范字段，并且读取的标记太大以致缓冲区中无法容纳，则不会向该缓冲区写入任何内容。  
  
 对于字符，可读取单个字符，如下所示：  
  
 `wchar_t wc;`  
  
 `swscanf_s(in_str, L"%c", &wc, 1);`  
  
 此示例从输入字符串读取单个字符，然后将其存储在宽字符缓冲区中。 在读取非 null 终止的字符串的多个字符时，将无符号整数用作宽度规范和缓冲区大小。  
  
 `char c[4];`  
  
 `sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated`  
  
 有关详细信息，请参阅 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 类型字段字符](../../c-runtime-library/scanf-type-field-characters.md)。  
  
> [!NOTE]
>  大小参数的类型具有 `unsigned`，而不具有 `size_t`。 当编译 64 位目标时，使用静态强制转换将 `_countof` 或 `sizeof` 结果转换为正确的大小。  
  
 `format` 参数控制输入字段的解释，并且格式和函数与 `scanf_s` 函数的 `format` 参数相同。 如果在重叠的字符串之间发生复制，则此行为不确定。  
  
 `swscanf_s` 是 `sscanf_s;` 的宽字符版本；`swscanf_s` 的参数是宽字符串。 `sscanf_s` 不处理多字节十六进制字符。 `swscanf_s` 不处理 Unicode 全角十六进制或“兼容区”字符。 除此以外，`swscanf_s` 和 `sscanf_s` 的行为完全相同。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_stscanf_s`|`sscanf_s`|`sscanf_s`|`swscanf_s`|  
|`_stscanf_s_l`|`_sscanf_s_l`|`_sscanf_s_l`|`_swscanf_s_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`sscanf_s`, `_sscanf_s_l`|\<stdio.h>|  
|`swscanf_s`, `_swscanf_s_l`|\<stdio.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_sscanf_s.c  
// This program uses sscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string plus NULL terminator  
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );  
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );  
   sscanf_s( tokenstring, "%d", &i );  
   sscanf_s( tokenstring, "%f", &fp );  
  
   // Output the data read  
   printf_s( "String    = %s\n", s );  
   printf_s( "Character = %c\n", c );  
   printf_s( "Integer:  = %d\n", i );  
   printf_s( "Real:     = %f\n", fp );  
}  
```  
  
```Output  
String    = 15  
Character = 1  
Integer:  = 15  
Real:     = 15.000000  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fscanf、_fscanf_l、fwscanf、_fwscanf_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf、_scanf_l、wscanf、_wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)
