---
title: "wcsrtombs | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcsrtombs
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
- wcsrtombs
dev_langs:
- C++
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 8dcf86093b363bd890e15ba7eb326a4187e65999
ms.lasthandoff: 02/24/2017

---
# <a name="wcsrtombs"></a>wcsrtombs
将宽字符字符串转换为多字节字符串表示形式。 此函数有一个更安全的版本；请参阅 [wcsrtombs_s](../../c-runtime-library/reference/wcsrtombs-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
size_t wcsrtombs(  
   char *mbstr,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcsrtombs(  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `mbstr`  
 生成的已转换多字节字符字符串的地址位置。  
  
 [in] `wcstr`  
 间接指向要转换的宽字符字符串的位置。  
  
 [in] `count`  
 要转换的字符数。  
  
 [in] `mbstate`  
 指向 `mbstate_t` 转换状态对象的指针。  
  
## <a name="return-value"></a>返回值  
 返回已成功转换的字节数，不包括 null 终止 null 字节（如果有），发生错误时则为 -1。  
  
## <a name="remarks"></a>备注  
 从 `mbstate` 中包含的指定转换状态开始，`wcsrtombs` 函数将 `wcstr` 中间接指向的宽字符字符串值转换为 `mbstr` 地址。 在遇到 null 终止宽字符或非相应字符或在下一个字符将超过 `count` 中的限制之前，每个字符的转换都将会一直进行。 如果 `wcsrtombs` 在 `count` 出现前或出现时遇到宽字符 null 字符 (L'\0')，则它将该字符转换为 8 位 0 并停止操作。  
  
 因此，只有当 `wcsrtombs` 在转换期间遇到宽字符 null 字符时，`mbstr` 处的多字节字符串才以 null 结尾。 如果 `wcstr` 和 `mbstr` 指向的序列重叠，则 `wcsrtombs` 的行为没有定义。 `wcsrtombs` 受到当前区域设置中 LC_TYPE 类别的影响。  
  
 `wcsrtombs` 函数的可重启性不同于 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)。 转换状态存储在 `mbstate` 中，以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用 `wcsrlen`（而非 `wcsnlen`）的后续调用，则应用程序应使用 `wcsrtombs`，而非 `wcstombs`。  
  
 如果 `mbstr` 参数为 `NULL`，则 `wcsrtombs` 会返回目标字符串所需的大小（以字节为单位）。 如果 `mbstate` 为 null，则使用内部 `mbstate_t` 转换状态。 如果字符序列 `wchar` 不具有相应的多字节字符表示形式，则返回 -1 且将 `errno` 设置为 `EILSEQ`。  
  
 在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>异常  
 只要当前线程中的函数都不调用 `setlocale`，此函数正在执行且 `mbstate` 不是 null，`wcsrtombs` 函数就是多线程安全的。  
  
## <a name="example"></a>示例  
  
```  
// crt_wcsrtombs.cpp  
// compile with: /W3  
// This code example converts a wide  
// character string into a multibyte  
// character string.  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
int main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    countConverted = wcsrtombs(mbString, &wcsIndirectString,  
                               MB_BUFFER_SIZE, &mbstate); // C4996  
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s  
    if (errno == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfuly converted.\n" );  
    }  
}  
```  
  
```Output  
The string was successfuly converted.  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`wcsrtombs`|\<wchar.h>|  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
