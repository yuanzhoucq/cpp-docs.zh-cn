---
title: "mbstowcs、_mbstowcs_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- mbstowcs
- _mbstowcs_l
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
- mbstowcs
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b422dbcb1d2fc07ff3fb1f00302b62da0500ebdc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="mbstowcs-mbstowcsl"></a>mbstowcs、_mbstowcs_l
将多字节字符序列转换为对应的宽字符序列。 提供这些函数的更多安全版本；请参阅 [mbstowcs_s、_mbstowcs_s_l](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)。  
  
## <a name="syntax"></a>语法  
  
```  
size_t mbstowcs(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count   
);  
size_t _mbstowcs_l(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t mbstowcs(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _mbstowcs_l(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `wcstr`  
 宽字符序列的地址。  
  
 [in] `mbstr`  
 Null 终止的多字节字符序列的地址。  
  
 [in] `count`  
 要转换的多字节字符的最大数量。  
  
 [in] `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果 `mbstowcs` 成功转换源字符串，则会返回经转换的多字节字符的数量。 如果 `wcstr` 参数为 `NULL`，此函数会返回目标字符串所需的大小（以宽字符为单位）。 如果`mbstowcs`遇到无效的多字节字符，则返回-1。 如果返回值为 `count`，则宽字符字符串不以 null 结尾。  
  
> [!IMPORTANT]
>  确保 `wcstr` 和 `mbstr` 未重叠，并且 `count` 正确反映了要转换的多字节字符的数量。  
  
## <a name="remarks"></a>备注  
 `mbstowcs` 函数最多可将 `mbstr` 指向的最大数量的 `count` 多字节字符转换为当前区域设置确定的相应的宽字符串。 它存储在表示的地址生成的宽字符字符串`wcstr`。 结果类似于对 `mbtowc` 的一系列调用。 如果在 `count` 发生之前或发生时 `mbstowcs` 遇到单字节空字符 ('\0')，则其将空字符转换为宽字符空字符 (L'\0') 然后停止。 因此，只有在转换期间遇到空字符时，`wcstr` 处的宽字符字符串才以 null 结尾。 如果 `wcstr` 和 `mbstr` 指向的序列重叠，则此行为没有定义。  
  
 如果 `wcstr` 参数是 `NULL`，则 `mbstowcs` 返回转换生成的宽字符数量，其中不包括 null 终止符。 源字符串必须以 null 结尾才能返回正确的值。 如果需要生成以 null 结尾的宽字符串，请向返回的值添加一个。  
  
 如果 `mbstr` 参数为 `NULL`，或者如果 `count` > `INT_MAX`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 errno 设置为 `EINVAL` 并返回 -1。  
  
 `mbstowcs` 将当前区域设置用于任何与区域设置相关的行为；`_mbstowcs_l` 与此相同，只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`mbstowcs`|\<stdlib.h>|  
|`_mbstowcs_l`|\<stdlib.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_mbstowcs.c  
// compile with: /W3  
// illustrates the behavior of the mbstowcs function  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main( void )  
{  
    size_t size;  
    int nChar = 2; // number of characters to convert  
    int requiredSize;  
  
    unsigned char    *pmbnull  = NULL;  
    unsigned char    *pmbhello = NULL;  
    char* localeInfo;  
  
    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters  
    wchar_t *pwc;  
  
    /* Enable the Japanese locale and codepage */  
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");  
    printf("Locale information set to %s\n", localeInfo);  
  
    printf( "Convert to multibyte string:\n" );  
  
    requiredSize = wcstombs( NULL, pwchello, 0); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    printf("  Required Size: %d\n", requiredSize);  
  
    /* Add one to leave room for the null terminator. */  
    pmbhello = (unsigned char *)malloc( requiredSize + 1);  
    if (! pmbhello)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    if (size == (size_t) (-1))  
    {  
        printf("Couldn't convert string. Code page 932 may"  
                " not be available.\n");  
        return 1;  
    }  
    printf( "  Number of bytes written to multibyte string: %u\n",  
            (unsigned int) size );  
    printf( "  Hex values of the " );  
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",  
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );  
    printf( "  Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");  
  
    printf( "Convert back to wide-character string:\n" );  
  
    /* Assume we don't know the length of the multibyte string.  
     Get the required size in characters, and allocate enough space. */  
  
    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996  
    /* Add one to leave room for the NULL terminator */  
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));  
    if (! pwc)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996  
    if (size == (size_t) (-1))  
    {  
       printf("Couldn't convert string--invalid multibyte character.\n");  
    }  
    printf( "  Characters converted: %u\n", (unsigned int)size );  
    printf( "  Hex value of first 2" );  
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );  
    free(pwc);  
    free(pmbhello);  
}  
```  
  
```Output  
Locale information set to Japanese_Japan.932  
Convert to multibyte string:  
  Required Size: 4  
  Number of bytes written to multibyte string: 4  
  Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1  
  Codepage 932 uses 0x81 to 0x9f as lead bytes.  
  
Convert back to wide-character string:  
  Characters converted: 2  
  Hex value of first 2 wide characters: 0x3042 0x3043  
```  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)