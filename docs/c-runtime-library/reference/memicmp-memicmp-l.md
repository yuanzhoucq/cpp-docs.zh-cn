---
title: "_memicmp、_memicmp_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _memicmp_l
- _memicmp
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _memicmp
- memicmp_l
- _memicmp_l
dev_langs:
- C++
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: e7547d6ff0e62e8bc4c449d55c5f06f1c9349092
ms.lasthandoff: 02/24/2017

---
# <a name="memicmp-memicmpl"></a>_memicmp、_memicmp_l
比较两个缓冲区中的字符（不区分大小写）。  
  
## <a name="syntax"></a>语法  
  
```  
int _memicmp(  
   const void *buf1,  
   const void *buf2,  
   size_t count   
);  
int _memicmp_l(  
   const void *buf1,  
   const void *buf2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `buf1`  
 第一个缓冲区。  
  
 `buf2`  
 第二个缓冲区。  
  
 `count`  
 字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 返回值指示缓冲区之间的关系。  
  
|返回值|buf1 和 buf2 的第一个计数字节的关系|  
|------------------|--------------------------------------------------------|  
|< 0|`buf1` 小于 `buf2`。|  
|0|`buf1` 等于 `buf2`。|  
|> 0|`buf1` 大于 `buf2`。|  
|`_NLSCMPERROR`|出现了错误。|  
  
## <a name="remarks"></a>备注  
 `_memicmp` 函数逐字节地比较两字节缓冲区 `count` 和 `buf1` 中的第一个 `buf2` 字符。 该比较不区分大小写。  
  
 如果 `buf1` 或 `buf2` 为 null 指针，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回 `_NLSCMPERROR`，并且将 `errno` 设置为 `EINVAL`。  
  
 `_memicmp` 将当前区域设置用于与区域设置相关的行为；`_memicmp_l` 也是一样，只不过它使用传入的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_memicmp`|\<memory.h> 或 \<string.h>|  
|`_memicmp_l`|\<memory.h> 或 \<string.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_memicmp.c  
// This program uses _memicmp to compare  
// the first 29 letters of the strings named first and  
// second without regard to the case of the letters.  
  
#include <memory.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   int result;  
   char first[] = "Those Who Will Not Learn from History";  
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";  
   // Note that the 29th character is right here ^  
  
   printf( "Compare '%.29s' to '%.29s'\n", first, second );  
   result = _memicmp( first, second, 29 );  
   if( result < 0 )  
      printf( "First is less than second.\n" );  
   else if( result == 0 )  
      printf( "First is equal to second.\n" );  
   else if( result > 0 )  
      printf( "First is greater than second.\n" );  
}  
```  
  
```Output  
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'  
First is equal to second.  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [缓冲区操作](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr、wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy、wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)
