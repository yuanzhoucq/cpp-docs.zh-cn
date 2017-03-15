---
title: "mbstowcs_s、_mbstowcs_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- _mbstowcs_s_l
- mbstowcs_s
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
caps.latest.revision: 31
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
ms.openlocfilehash: 3a5c84be1336d762289705102c1f2213f04642ea
ms.lasthandoff: 02/24/2017

---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l
将多字节字符序列转换为对应的宽字符序列。 这些版本的 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count   
);  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `pReturnValue`  
 要转换的字符数。  
  
 [out] `wcstr`  
 用于转换所生成的宽字符串的缓冲区地址。  
  
 [in] `sizeInWords`  
 `wcstr` 缓冲区大小（以字数为单位）。  
  
 [in]`mbstr`  
 Null 终止的多字节字符序列的地址。  
  
 [in] `count`  
 要存储在 `wcstr` 缓冲区中的宽字符的最大数量，不包括终止 null 或 [_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 [in] `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回零；如果失败，则返回错误代码。  
  
|错误条件|返回值和 `errno`|  
|---------------------|------------------------------|  
|`wcstr` 是 `NULL` 和 `sizeInWords` > 0|`EINVAL`|  
|`mbstr` 为 `NULL`|`EINVAL`|  
|目标缓冲区过小，无法包含转换的字符串（除非 `count` 是 `_TRUNCATE`；请参阅下面的备注）|`ERANGE`|  
|`wcstr` 不是 `NULL` 且 `sizeInWords` == 0|`EINVAL`|  
  
 如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，函数将返回错误代码并按表中所示设置 `errno`。  
  
## <a name="remarks"></a>备注  
 `mbstowcs_s` 函数将 `mbstr` 指向的多字节字符串转换为存储在 `wcstr` 指向的缓冲区中的宽字符。 在满足以下条件之一前，该转换将一直对每个字符执行：  
  
-   遇到一个多字节空字符  
  
-   遇到一个无效的多字节字符  
  
-   存储在 `wcstr` 缓冲区中的宽字符数等于 `count`。  
  
 目标字符串始终以 null 结尾（即使在出错时）。  
  
 如果 `count` 是特殊值 [_TRUNCATE](../../c-runtime-library/truncate.md)，则 `mbstowcs_s` 会根据目标缓冲区的容量尽量多地转换字符串，同时仍然为 null 终止符留下空间。  
  
 如果 `mbstowcs_s` 成功转换了源字符串，它会将转换的字符串（包括 null 终止符）的大小（以宽字符为单位）放入 `*``pReturnValue`（假定 `pReturnValue` 不是 `NULL`）。 即使 `wcstr` 参数为 `NULL` 并提供了确定所需的缓冲区大小的方法，也会发生这种情况。 请注意，如果 `wcstr` 为 `NULL`，则 `count` 会被忽略，且 `sizeInWords` 必须为 0。  
  
 如果 `mbstowcs_s` 遇到无效的多字节字符，它将执行以下操作：将 0 放入 `*``pReturnValue`，将目标缓冲区设置为空字符串，将 `errno` 设置为 `EILSEQ`，并返回 `EILSEQ`。  
  
 如果 `mbstr` 和 `wcstr` 指向的序列重叠，则 `mbstowcs_s` 的行为没有定义。  
  
> [!IMPORTANT]
>  确保 `wcstr` 和 `mbstr` 未重叠，并且 `count` 正确反映了要转换的多字节字符的数量。  
  
 `mbstowcs_s` 将当前区域设置用于任何与区域设置相关的行为；`_mbstowcs_s_l` 与此相同，只不过它使用传入的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`mbstowcs_s`|\<stdlib.h>|  
|`_mbstowcs_s_l`|\<stdlib.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)
