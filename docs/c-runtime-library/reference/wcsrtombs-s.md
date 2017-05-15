---
title: "wcsrtombs_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcsrtombs_s
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
- wcsrtombs_s
dev_langs:
- C++
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
caps.latest.revision: 27
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
ms.openlocfilehash: 4c32ff2061e8ce52ae193c7679b40e69515d3ab0
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="wcsrtombss"></a>wcsrtombs_s
将宽字符字符串转换为多字节字符串表示形式。 [wcsrtombs](../../c-runtime-library/reference/wcsrtombs.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `pReturnValue`  
 要转换的字符数。  
  
 [out] `mbstr`  
 生成的已转换多字节字符字符串的缓冲区的地址。  
  
 [out] `sizeInBytes`  
 缓冲区 `mbstr` 的大小（以字节为单位）。  
  
 [in] `wcstr`  
 指向要转换的宽字符字符串的指针。  
  
 [in] `count`  
 `mbstr` 缓冲区或 [_TRUNCATE](../../c-runtime-library/truncate.md) 要存储的最大字节数。  
  
 [in] `mbstate`  
 指向 `mbstate_t` 转换状态对象的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回零；如果失败，则返回错误代码。  
  
|错误条件|返回值和 `errno`|  
|---------------------|------------------------------|  
|`mbstr` 是 `NULL` 和 `sizeInBytes` > 0|`EINVAL`|  
|`wcstr` 为 `NULL`|`EINVAL`|  
|目标缓冲区过小，无法包含转换的字符串（除非 `count` 是 `_TRUNCATE`；请参阅下面的备注）|`ERANGE`|  
  
 如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，函数将返回错误代码并按表中所示设置 `errno`。  
  
## <a name="remarks"></a>备注  
 `wcsrtombs_s` 函数通过使用 `mbstate` 中包含的转换状态，将由 `wcstr` 指向的宽字符的字符串转换为 `mbstr` 指向的缓冲区中存储的多字节字符。 在满足以下条件之一前，该转换将一直对每个字符执行：  
  
-   遇到 null 宽字符  
  
-   遇到无法转换的宽字符  
  
-   存储在 `mbstr` 缓冲中的字节数等于 `count`。  
  
 目标字符串始终以 null 结尾（即使在出错时）。  
  
 如果 `count` 是特殊值 [_TRUNCATE](../../c-runtime-library/truncate.md)，则 `wcsrtombs_s` 会根据目标缓冲区的容量尽量多地转换字符串，同时仍然为 null 终止符留下空间。  
  
 如果 `wcsrtombs_s` 成功转换了源字符串，它会将转换的字符串（包括 null 终止符）的大小（以字节为单位）放入 `*``pReturnValue`（假定 `pReturnValue` 不是 `NULL`）。 即使 `mbstr` 参数为 `NULL` 并提供了确定所需的缓冲区大小的方法，也会发生这种情况。 请注意，如果 `mbstr` 为 `NULL`，则 `count` 会被忽略。  
  
 如果 `wcsrtombs_s` 遇到无法转换为多字节字符的宽字符，将会把 -1 放入 `*``pReturnValue`，并将目标缓冲区设置为空字符串，将 `errno` 设置为 `EILSEQ`，并返回 `EILSEQ`。  
  
 如果 `wcstr` 和 `mbstr` 指向的序列重叠，则 `wcsrtombs_s` 的行为没有定义。 `wcsrtombs_s` 受到当前区域设置中 LC_TYPE 类别的影响。  
  
> [!IMPORTANT]
>  请确保 `wcstr` 和 `mbstr` 未重叠，并且 `count` 正确地反映了要转换的宽字节的数量。  
  
 `wcsrtombs_s` 函数的可重启性不同于 [wcstombs_s、_wcstombs_s_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)。 转换状态存储在 `mbstate` 中，以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用 `wcsrlen`（而非 `wcslen`）的后续调用，则应用程序应使用 `wcsrtombs_s`，而非 `wcstombs_s.`  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>异常  
 只要当前线程中的函数都不调用 `setlocale`，此函数正在执行且 `mbstate` 是 null，`wcsrtombs_s` 函数就是多线程安全的。  
  
## <a name="example"></a>示例  
  
```  
// crt_wcsrtombs_s.cpp  
//   
// This code example converts a wide  
// character string into a multibyte  
// character string.  
//  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
void main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    errno_t         err;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,  
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);  
    if (err == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfully converted.\n" );  
    }  
}  
```  
  
```Output  
The string was successfully converted.  
```  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`wcsrtombs_s`|\<wchar.h>|  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
