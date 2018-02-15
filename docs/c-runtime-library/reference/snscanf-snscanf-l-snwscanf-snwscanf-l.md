---
title: "_snscanf、_snscanf_l、_snwscanf、_snwscanf_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _snwscanf
- _snscanf_l
- _snscanf
- _snwscanf_l
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
- _snscanf
- _snscanf_l
- _snwscanf
- snscanf_l
- snscanf
- _sntscanf_l
- _sntscanf
- _snwscanf_l
- sntscanf_l
- sntscanf
- snwscanf
- snwscanf_l
dev_langs:
- C++
helpviewer_keywords:
- snscanf_l function
- snwscanf function
- _sntscanf_l function
- sntscanf function
- _snwscanf_l function
- _sntscanf function
- _snscanf_l function
- sntscanf_l function
- strings [C++], reading data from
- snscanf function
- snwscanf_l function
- _snwscanf function
- reading data, strings
- strings [C++], reading
- _snscanf function
ms.assetid: da1ac890-f905-4cd7-954b-3c90957b5551
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37ebbde63bec1ef670e4e0bf9596c2e59aa5fcc5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="snscanf-snscanfl-snwscanf-snwscanfl"></a>_snscanf、_snscanf_l、_snwscanf、_snwscanf_l
从字符串中读取指定长度的格式化数据。 提供这些函数的更多安全版本；请参阅 [_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l](../../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)。  
  
## <a name="syntax"></a>语法  
  
```  
int __cdecl _snscanf(  
   const char * input,  
   size_t length,  
   const char * format,  
   ...  
);  
int __cdecl _snscanf_l(  
   const char * input,  
   size_t length,  
   const char * format,  
   locale_t locale,  
   ...  
);  
int __cdecl _snwscanf(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   ...  
);  
int __cdecl _snwscanf_l(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   locale_t locale,  
   ...  
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
  
## <a name="return-value"></a>返回值  
 这两个函数都将返回已成功转换并分配的字段的数目；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 如果在首次转换前到达字符串的结尾，则返回值为 `EOF` 以指示错误。 有关详细信息，请参阅 [sscanf](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)。  
  
 如果 `input` 或 `format` 是一个 `NULL` 指针，或如果 `length` 小于或等于 0，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 此函数与 `sscanf` 类似，只不过它可以指定要在输入字符串检查的固定数量的字符。 有关详细信息，请参阅 [sscanf](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_sntscanf`|`_snscanf`|`_snscanf`|`_snwscanf`|  
|`_sntscanf_l`|`_snscanf_l`|`_snscanf_l`|`_snwscanf_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_snscanf`, `_snscanf_l`|\<stdio.h>|  
|`_snwscanf`, `_snwscanf_l`|\<stdio.h> 或 \<wchar.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_snscanf.c  
// compile with: /W3  
  
#include <stdio.h>  
int main( )  
{  
   char  str1[] = "15 12 14...";  
   wchar_t  str2[] = L"15 12 14...";  
   char  s1[3];  
   wchar_t  s2[3];  
   int   i;  
   float fp;  
  
   i = _snscanf( str1, 6,  "%s %f", s1, &fp); // C4996  
   // Note: _snscanf is deprecated; consider using _snscanf_s instead  
   printf("_snscanf converted %d fields: ", i);  
   printf("%s and %f\n", s1, fp);  
  
   i = _snwscanf( str2, 6,  L"%s %f", s2, &fp); // C4996  
   // Note: _snwscanf is deprecated; consider using _snwscanf_s instead  
   wprintf(L"_snwscanf converted %d fields: ", i);  
   wprintf(L"%s and %f\n", s2, fp);  
}  
```  
  
```Output  
_snscanf converted 2 fields: 15 and 12.000000  
_snwscanf converted 2 fields: 15 and 12.000000  
```  
  
## <a name="see-also"></a>请参阅  
 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)