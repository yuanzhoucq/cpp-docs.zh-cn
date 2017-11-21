---
title: "mbsrtowcs | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbsrtowcs
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
f1_keywords: mbsrtowcs
dev_langs: C++
helpviewer_keywords: mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e2e3a202eb50159c43c57c96f785c74156336af8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="mbsrtowcs"></a>mbsrtowcs
将当前区域设置中的多字节字符字符串转换为相应的宽字符字符串，其中重启功能位于多字节字符的中间。 提供此函数的一个更安全的版本；请参阅 [mbsrtowcs_s](../../c-runtime-library/reference/mbsrtowcs-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
size_t mbsrtowcs(  
   wchar_t *wcstr,  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t mbsrtowcs(  
   wchar_t (&wcstr)[size],  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `wcstr`  
 用于存储转换生成的宽字符字符串的地址。  
  
 [in, out] `mbstr`  
 指向要转换的多字节字符字符串位置的间接指针。  
  
 [in] `count`  
 要转换并将存储在 `wcstr` 中的最大字符（非字节）数。  
  
 [in, out] `mbstate`  
 指向 `mbstate_t` 转换状态对象的指针。 如果此值为 null 指针，则使用静态内部转换状态对象。 由于内部 `mbstate_t` 对象不是线程安全的，建议始终传递你自己的 `mbstate` 参数。  
  
## <a name="return-value"></a>返回值  
 返回成功转换的字符数，不包括终止 null 字符（若有）。 如果错误发生，则返回 (size_t)(-1)，并将 `errno` 设置为 EILSEQ。  
  
## <a name="remarks"></a>备注  
 `mbsrtowcs` 函数通过使用 `mbstr` 中包含的转换状态，将由 `wcstr` 间接指向的多字节字符的字符串转换缓冲区中所存储的由 `mbstate` 指向的宽字符。 将继续执行对每个字符的转换，直至遇到终止 null 多字节字符、遇到与当前区域设置中的有效字符不对应的多字节序列，或直至完成对 `count` 个字符的转换。 如果 `mbsrtowcs` 在 `count` 出现前或出现时遇到多字节 null 字符（“\0”），则它将该字符转换为 16 位终止 null 字符并停止操作。  
  
 因此，只有当 `wcstr` 在转换期间遇到多字节 null 字符时，`mbsrtowcs` 处的宽字符才以 null 结尾。 如果 `mbstr` 和 `wcstr` 指向的序列重叠，则 `mbsrtowcs` 的行为没有定义。 `mbsrtowcs` 受到当前区域设置中 LC_TYPE 类别的影响。  
  
 `mbsrtowcs` 函数的可重启性不同于 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)。 转换状态存储在 `mbstate` 中，以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用 `mbsrlen`（而非 `mbslen`）的后续调用，则应用程序应使用 `mbsrtowcs`，而不是 `mbstowcs.`。  
  
 如果 `wcstr` 不是 null 指针，则在转换因到达终止 null 字符而停止时，`mbstr` 指向的指针对象将分配到一个 null 指针。 否则，它将分配到紧跟已转换出的最后一个多字节字符的地址（若有）。 这将允许调用后续函数以在此调用停止的位置重新调用转换。  
  
 如果 `wcstr` 参数为 null 指针，则忽略 `count` 参数，且 `mbsrtowcs` 以宽字符形式返回目标字符串所需的大小。 如果 `mbstate` 为 null 指针，则该函数将使用非线程安全的静态内部 `mbstate_t` 转换状态对象。 如果字符序列 `mbstr` 不具有相应的多字节字符表示形式，则返回 -1 且将 `errno` 设置为 `EILSEQ`。  
  
 如果 `mbstr` 是空指针，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
 在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>异常  
 只要当前线程中的函数都不调用 `mbsrtowcs`、此函数正在执行且 `setlocale` 参数不是 null 指针，`mbstate` 函数就是多线程安全的。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`mbsrtowcs`|\<wchar.h>|  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)