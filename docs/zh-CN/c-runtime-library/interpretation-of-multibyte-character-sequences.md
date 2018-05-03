---
title: 多字节字符序列的解释 | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- c.character.multibyte
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1363d5fd28f7a8c3cbf01c24db028bad38185364
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="interpretation-of-multibyte-character-sequences"></a>多字节字符序列的解释

Microsoft 运行库中的大多数多字节字符例程可识别与多字节代码页相关的多字节字符序列。 输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。

## <a name="locale-dependent-multibyte-routines"></a>与区域设置相关的多字节例程

|例程所返回的值|使用|
|-------------|---------|
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|验证并返回多字节字符中的字节数|
|[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|对于多字节字符串：验证字符串中的每个字符；返回字符串的长度。 对于宽字符字符串：返回字符串长度。|
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|将多字节字符序列转换为对应的宽字符序列|
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|将多字节字符转换为对应的宽字符|
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|将宽字符序列转换为相应的多字节字符序列|
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|将宽字符转换为相应的多字节字符|
|[mbrtoc16、mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|将多字节字符转换为等效 UTF-16 或 UTF-32 字符|
|[c16rtomb、c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|将 UTF-16 或 UTF-32 字符转换为等效多字节字符|

## <a name="see-also"></a>请参阅

[国际化](../c-runtime-library/internationalization.md)<br/>
 [按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
