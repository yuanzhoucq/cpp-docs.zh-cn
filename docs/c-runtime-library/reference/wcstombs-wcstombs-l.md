---
title: "wcstombs、_wcstombs_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstombs
- _wcstombs_l
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
- wcstombs
- _wcstombs_l
dev_langs:
- C++
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
caps.latest.revision: 30
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
ms.openlocfilehash: dead533ee11db7c40faa7d3611b30c6a6159ee50
ms.lasthandoff: 02/24/2017

---
# <a name="wcstombs-wcstombsl"></a>wcstombs、_wcstombs_l
将宽字符序列转换为对应的多字节字符序列。 提供这些函数的更多安全版本；请参阅 [wcstombs_s、_wcstombs_s_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)。  
  
## <a name="syntax"></a>语法  
  
```  
size_t wcstombs(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count   
);  
size_t _wcstombs_l(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t wcstombs(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _wcstombs_l(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `mbstr`  
 多字节字符序列的地址。  
  
 `wcstr`  
 宽字符序列的地址。  
  
 `count`  
 多字节输出字符串可以存储的最大字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果 `wcstombs` 成功转换多字节字符串，将返回多字节输出字符串中写入的字节数，不包括终止 `NULL`（如果有）。 如果 `mbstr` 参数为 `NULL`，则 `wcstombs` 会返回目标字符串所需的大小（以字节为单位）。 如果 `wcstombs` 遇到无法转换为多字节字符的宽字符，将会把 -1 强制转换为类型 `size_t`，并将 `errno` 设置为 `EILSEQ`。  
  
## <a name="remarks"></a>备注  
 `wcstombs` 函数将 `wcstr` 指向的宽字符字符串转换为相应的多字节字符，并将转换结果存储到 `mbstr` 数组中。 `count` 参数指明多字节输出字符串可以存储的最大字节数（也就是 `mbstr` 的大小）。 一般情况下，转换宽字符字符串时不会知道需要多少个字节。 某些宽字符在输出字符串中仅占一个字节；其他的字符则占两个。 如果输入字符串每个宽字符的多字节输出字符串存在两个字节（包括宽字符 `NULL`），要确保结果可以将其容纳。  
  
 如果 `wcstombs` 在 `count` 出现前或出现时遇到宽字符 null 字符 (L'\0')，则它将该字符转换为 8 位 0 并停止操作。 因此，只有当 `wcstombs` 在转换期间遇到宽字符 null 字符时，`mbstr` 处的多字节字符串才以 null 结尾。 如果 `wcstr` 和 `mbstr` 指向的序列重叠，则 `wcstombs` 的行为没有定义。  
  
 如果 `mbstr` 参数为 `NULL`，则 `wcstombs` 会返回目标字符串所需的大小（以字节为单位）。  
  
 `wcstombs` 会验证其参数。 如果 `wcstr` 为 `NULL`，或如果 `count` 优于 `INT_MAX`，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则该函数将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
 `wcstombs` 将当前区域设置用于任何与区域设置相关的行为；`_wcstombs_l` 与此相同，只不过它使用传入的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`wcstombs`|\<stdlib.h>|  
|`_wcstombs_l`|\<stdlib.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 本程序演示 `wcstombs` 函数的行为。  
  
```  
// crt_wcstombs.c  
// compile with: /W3  
// This example demonstrates the use  
// of wcstombs, which converts a string  
// of wide characters to a string of   
// multibyte characters.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t  count;  
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t *pWCBuffer = L"Hello, world.";  
  
    printf("Convert wide-character string:\n" );  
  
    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s instead  
    printf("   Characters converted: %u\n",  
            count );  
    printf("    Multibyte character: %s\n\n",  
           pMBBuffer );  
  
    free(pMBBuffer);  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 13  
    Multibyte character: Hello, world.  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)
