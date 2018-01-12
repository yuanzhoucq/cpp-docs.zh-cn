---
title: "wcrtomb_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wcrtomb_s
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
f1_keywords: wcrtomb_s
dev_langs: C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13134a3e6b34be13d6d878cf94f204bb6c87a458
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wcrtombs"></a>wcrtomb_s
将宽字符转换为多字节字符表示形式。 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char *mbchar,  
   size_t sizeOfmbchar,  
   wchar_t *wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char (&mbchar)[size],  
   wchar_t *wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `pReturnValue`  
 返回写入的字节数，如果发生错误，则返回 -1。  
  
 [out] `mbchar`  
 生成的多字节转换字符。  
  
 [in] `sizeOfmbchar`  
 `mbchar` 变量的大小（以字节为单位）。  
  
 [in] `wchar`  
 要转换的宽字符。  
  
 [in] `mbstate`  
 指向 `mbstate_t` 对象的指针。  
  
## <a name="return-value"></a>返回值  
 返回零，如果发生错误，则返回 `errno` 值。  
  
## <a name="remarks"></a>备注  
 从 `mbstate` 中包含的指定转换状态开始，`wcrtomb_s` 函数将 `wchar` 的宽字符值转换为 `mbchar` 表示的地址。 `pReturnValue` 值是转换的字节数，但不能超过 `MB_CUR_MAX` 字节，发生错误时该值为 -1。  
  
 如果 `mbstate` 为 null，则使用内部 `mbstate_t` 转换状态。 如果 `wchar` 包含的字符不具有相应的多字节字符，则 `pReturnValue` 值将为 -1 且函数将返回 `EILSEQ` 的 `errno` 值。  
  
 `wcrtomb_s` 函数的可重启性不同于 [wctomb_s、_wctomb_s_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)。 转换状态存储在 `mbstate` 中，以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用 `wcsrlen`（而非 `wcslen`）的后续调用，则应用程序应使用 `wcsrtombs_s`，而非 `wcstombs_s.`  
  
 在 C++ 中，模板重载简化了此函数的使用；重载可以自动推导出缓冲区长度（不再需要指定大小自变量），并且它们可以自动用更新、更安全的对应物替换不安全的旧函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>异常  
 只要当前线程中的函数都不调用 `setlocale`，此函数正在执行且 `mbstate` 是 null，`wcrtomb_s` 函数就是多线程安全的。  
  
## <a name="example"></a>示例  
  
```  
// crt_wcrtomb_s.c  
// This program converts a wide character  
// to its corresponding multibyte character.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    errno_t     returnValue;  
    size_t      pReturnValue;  
    mbstate_t   mbstate;  
    size_t      sizeOfmbStr = 1;  
    char        mbchar = 0;  
    wchar_t*    wchar = L"Q\0";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),  
                            *wchar, &mbstate);  
    if (returnValue == 0) {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wchar);  
        printf(" was converted to a the \"%c\" ", mbchar);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
```Output  
The corresponding wide character "Q" was converted to a the "Q" multibyte character.  
```  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`wcrtomb_s`|\<wchar.h>|  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)