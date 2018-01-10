---
title: "wcstombs_s、_wcstombs_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcstombs_s_l
- wcstombs_s
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
- wcstombs_s
- _wcstombs_s_l
dev_langs: C++
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5c57a82bef1a56925b414302fe2017df255ce2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wcstombss-wcstombssl"></a>wcstombs_s、_wcstombs_s_l

将宽字符序列转换为对应的多字节字符序列。 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count   
);  

errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  

template <size_t size>  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  

template <size_t size>  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  

[out]*pReturnValue*  
要转换的字符数。  
  
[out]*mbstr*  
生成的已转换多字节字符字符串的缓冲区的地址。  
  
[in]*sizeInBytes*  
以字节为单位的大小*mbstr*缓冲区。  
  
[in]*wcstr*  
指向要转换的宽字符字符串的指针。  
  
[in]*计数*  
最大存储中的字节数*mbstr*缓冲区，不包括终止 null 字符，或[_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
[in]*区域设置*  
要使用的区域设置。  
  
## <a name="return-value"></a>返回值  

如果成功，返回零；如果失败，则返回错误代码。  
  
|错误条件|返回值和 `errno`|  
|---------------------|------------------------------|  
|*mbstr*是`NULL`和*sizeInBytes* > 0|`EINVAL`|  
|*wcstr*是`NULL`|`EINVAL`|  
|目标缓冲区是太小，无法包含转换的字符串 (除非*计数*是`_TRUNCATE`; 请参阅下面的备注)|`ERANGE`|  
  
如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，函数将返回错误代码并按表中所示设置 `errno`。  
  
## <a name="remarks"></a>备注  

`wcstombs_s`函数将指向的宽字符字符串转换*wcstr*到存储指向的缓冲区中的多字节字符*mbstr*。 在满足以下条件之一前，该转换将一直对每个字符执行：  
  
-   遇到 null 宽字符  
  
-   遇到无法转换的宽字符  
  
-   存储中的字节数*mbstr*缓冲等于*计数*。  
  
目标字符串始终以 null 结尾（即使在出错时）。  
  
如果*计数*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)，然后`wcstombs_s`将尽可能多的字符串作为将放入目标缓冲区中，同时仍保持 null 终止符的空间。 如果字符串被截断，则返回值是`STRUNCATE`，和转换仍被视为成功。  
  
如果`wcstombs_s`成功转换了源字符串，它会将大小，以字节为单位的转换的字符串，包括 null 终止符，更改为`*pReturnValue`(提供*pReturnValue*不`NULL`)。 发生这种情况即使*mbstr*自变量是`NULL`，并提供了一种方法来确定所需的缓冲区大小。 请注意，如果*mbstr*是`NULL`，*计数*将被忽略。  
  
如果 `wcstombs_s` 遇到无法转换为多字节字符的宽字符，将会把 0 放入 `*pReturnValue`，并将目标缓冲区设置为空字符串，将 `errno` 设置为 `EILSEQ`，并返回 `EILSEQ`。  
  
如果指向的序列*wcstr*和*mbstr*重叠的行为`wcstombs_s`是不确定的。  
  
> [!IMPORTANT]
>  确保*wcstr*和*mbstr*未重叠，且*计数*正确地反映了要转换的宽字符数。  
  
`wcstombs_s` 对所有区域设置相关行为使用当前区域设置；`_wcstombs_s_l` 与 `wcstombs` 相同，只不过前者使用的是传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`wcstombs_s`|\<stdlib.h>|  
  
有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  

本程序演示 `wcstombs_s` 函数的行为。  
  
```C  
// crt_wcstombs_s.c  
// This example converts a wide character  
// string to a multibyte character string.  
#include <stdio.h>  
#include <stdlib.h>  
#include <assert.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t   i;  
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t*pWCBuffer = L"Hello, world.";  
  
    printf( "Convert wide-character string:\n" );  
  
    // Conversion  
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,   
               pWCBuffer, (size_t)BUFFER_SIZE );  
  
    // Output  
    printf("   Characters converted: %u\n", i);  
    printf("    Multibyte character: %s\n\n",  
     pMBBuffer );  
  
    // Free multibyte character buffer  
    if (pMBBuffer)  
    {  
    free(pMBBuffer);  
    }  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 14  
    Multibyte character: Hello, world.  
```  
  
## <a name="see-also"></a>请参阅  

[数据转换](../../c-runtime-library/data-conversion.md)   
[区域设置](../../c-runtime-library/locale.md)   
[_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
[mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
[mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
[wctomb_s、_wctomb_s_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)   
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)