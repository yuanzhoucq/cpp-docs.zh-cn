---
title: "_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _snwscanf_s_l
- _snwscanf_s
- _snscanf_s
- _snscanf_s_l
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
- _sntscanf_s
- snscanf_s
- _snwscanf_s_l
- sntscanf_s_l
- snwscanf_s_l
- snwscanf_s
- _snscanf_s
- _snwscanf_s
- snscanf_s_l
- _sntscanf_s_l
- _snscanf_s_l
- sntscanf_s
dev_langs: C++
helpviewer_keywords:
- _snscanf_s_l function
- snwscanf_s function
- _snwscanf_s function
- sntscanf_s_l function
- sntscanf_s function
- _snwscanf_s_l function
- _snscanf_s function
- snscanf_s_l function
- strings [C++], reading data from
- _sntscanf_s_l function
- reading data, strings
- snscanf_s function
- strings [C++], reading
- _sntscanf_s function
- snwscanf_s_l function
ms.assetid: 72356653-7362-461a-af73-597b9c0a8094
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71c771c20256053b9bb6da0751bbde761e66d678
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="snscanfs-snscanfsl-snwscanfs-snwscanfsl"></a>_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l
从字符串中读取指定长度的格式化数据。 这些版本的 [_snscanf、_snscanf_l、_snwscanf、_snwscanf_l](../../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## <a name="syntax"></a>语法  
  
```  
int __cdecl _snscanf_s(  
   const char * input,  
   size_t length,  
   const char * format [, argument_list]  
);  
int __cdecl _snscanf_s_l(  
   const char * input,  
   size_t length,  
   const char * format,  
   locale_t locale [, argument_list]
);  
int __cdecl _snwscanf_s(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format [, argument_list]
);  
int __cdecl _snwscanf_s_l(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   locale_t locale [, argument_list]
);  
```  
  
#### <a name="parameters"></a>参数  
 `input`  
 要检查的输入字符串。  
  
 `length`  
 `input` 中要检查的字符数。  
  
 `format`  
 一个或多个格式说明符。  
  
 `... (optional)`  
 将用于存储通过 `format` 中的格式说明符从输入字符串中提取的值的变量。  
  
 `locale`  
 要使用的区域设置。  
  
 `argument_list`  
 要分配根据格式字符串的可选自变量。  
  
## <a name="return-value"></a>返回值  
 这两个函数都将返回已成功转换并分配的字段的数目；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 如果在首次转换前到达字符串的结尾，则返回值为 `EOF` 以指示错误。 有关详细信息，请参阅 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。  
  
 如果 `input` 或 `format` 是 `NULL` 指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 此函数与 `sscanf_s` 类似，只不过它可以指定要在输入字符串检查的固定数量的字符。 有关详细信息，请参阅 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。  
  
 缓冲区大小参数需要与类型字段字符 `c`、`C`、`s`、`S` 和 `[` 一起使用。 有关详细信息，请参阅 [scanf 类型字段字符](../../c-runtime-library/scanf-type-field-characters.md)。  
  
> [!NOTE]
>  大小参数的类型具有 `unsigned`，而不具有 `size_t`。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_sntscanf_s`|`_snscanf_s`|`_snscanf_s`|`_snwscanf_s`|  
|`_sntscanf_s_l`|`_snscanf_s_l`|`_snscanf_s_l`|`_snwscanf_s_l`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_snscanf_s`, `_snscanf_s_l`|\<stdio.h>|  
|`_snwscanf_s`, `_snwscanf_s_l`|\<stdio.h> 或 \<wchar.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_snscanf_s.c  
// This example scans a string of   
// numbers, using both the character  
// and wide character secure versions  
// of the snscanf function.  
  
#include <stdio.h>  
  
int main( )  
{  
    char        str1[] = "15 12 14...";  
    wchar_t     str2[] = L"15 12 14...";  
    char        s1[3];  
    wchar_t     s2[3];  
    int         i;  
    float       fp;  
  
    i = _snscanf_s( str1, 6,  "%s %f", s1, 3, &fp);  
    printf_s("_snscanf_s converted %d fields: ", i);  
    printf_s("%s and %f\n", s1, fp);  
  
    i = _snwscanf_s( str2, 6,  L"%s %f", s2, 3, &fp);  
    wprintf_s(L"_snwscanf_s converted %d fields: ", i);  
    wprintf_s(L"%s and %f\n", s2, fp);  
}  
```  
  
```Output  
_snscanf_s converted 2 fields: 15 and 12.000000  
_snwscanf_s converted 2 fields: 15 and 12.000000  
```  
  
## <a name="see-also"></a>请参阅  
 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)