---
title: "wctomb_s、_wctomb_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wctomb_s_l
- wctomb_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctomb_s
- _wctomb_s_l
dev_langs: C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3c819f62f36966363f32eb16b7af758de274d3d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wctombs-wctombsl"></a>wctomb_s、_wctomb_s_l
将一个宽字符转换为相应的多字节字符。 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t wctomb_s(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar   
);  
errno_t _wctomb_s_l(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 [out] `pRetValue`  
 字节数或指明结果的代码。  
  
 [out] `mbchar`  
 多字节字符的地址。  
  
 [in] `sizeInBytes`  
 缓冲区 `mbchar` 的大小。  
  
 [in] `wchar`  
 宽字符。  
  
 [in] `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回零；如果失败，则返回错误代码。  
  
 错误条件  
  
|`mbchar`|`sizeInBytes`|返回值|`pRetValue`|  
|--------------|-------------------|------------------|-----------------|  
|`NULL`|>0|`EINVAL`|未修改|  
|任何|>`INT_MAX`|`EINVAL`|未修改|  
|任何|过小|`EINVAL`|未修改|  
  
 如果发生上述错误情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则 `wctomb` 返回 `EINVAL`，并将 `errno` 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `wctomb_s` 函数将 `wchar` 参数转换为相应的多字节字符并将转换结果存储到 `mbchar`。 可以从任何程序的任何程序点调用该函数。  
  
 如果 `wctomb_s` 将宽字符转换为多字节字符，则会将宽字符的字节数（始终不大于 `MB_CUR_MAX`）放入 `pRetValue` 指向的整数。 如果 `wchar` 为宽字符 null 字符 (L'\0')，`wctomb_s` 会将 1 填充到 `pRetValue`。 如果目标指针 `mbchar` 为 NULL，`wctomb_s` 会将 0 放入 `pRetValue`。 如果转换不在当前区域设置，可能`wctomb_s`-1 放`pRetValue`。  
  
 `wctomb_s` 将当前区域设置用于与区域设置相关的信息；`_wctomb_s_l` 也是一样，只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`wctomb_s`|\<stdlib.h>|  
|`_wctomb_s_l`|\<stdlib.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 本程序演示 `wctomb` 函数的行为。  
  
```  
// crt_wctomb_s.cpp  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    int i;  
    wchar_t wc = L'a';  
    char *pmb = (char *)malloc( MB_CUR_MAX );  
  
    printf_s( "Convert a wide character:\n" );  
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );  
    printf_s( "   Characters converted: %u\n", i );  
    printf_s( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
```Output  
Convert a wide character:  
   Characters converted: 1  
   Multibyte character: a  
```  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)