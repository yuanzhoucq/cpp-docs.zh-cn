---
title: 多字节字符序列的解释
ms.date: 10/22/2019
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
ms.openlocfilehash: 7431f0c63df60414af192ea38103318c775c430d
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811086"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>多字节字符序列的解释

Microsoft 运行库中的大多数多字节字符例程可识别与多字节代码页相关的多字节字符序列。 输出值受区域设置的**LC_CTYPE**类别设置的设置影响。 有关详细信息，请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 **_l**后缀的函数的版本对与区域设置相关的行为使用当前区域设置。 带有 **_l**后缀的版本是相同的，只不过它们使用区域设置参数而不是当前区域设置。

## <a name="locale-dependent-multibyte-routines"></a>与区域设置相关的多字节例程

|例程所返回的值|使用“管理”工作区中的“连接的管理组”|
|-------------|---------|
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|验证并返回多字节字符中的字节数|
|[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|对于多字节字符串：验证字符串中的每个字符；返回字符串的长度。 对于宽字符字符串：返回字符串长度。|
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|将多字节字符序列转换为对应的宽字符序列|
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|将多字节字符转换为对应的宽字符|
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|将宽字符序列转换为相应的多字节字符序列|
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|将宽字符转换为相应的多字节字符|

## <a name="locale-independent-multibyte-routines"></a>独立于区域设置的多字节例程

|例程所返回的值|使用“管理”工作区中的“连接的管理组”|
|-------------|---------|
|[mbrtoc16、mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|将多字节 UTF-8 字符转换为等效的 UTF-16 或 UTF-32 字符|
|[c16rtomb、c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|将 UTF-16 或 UTF-32 字符转换为等效的 UTF-8 多字节字符|

## <a name="see-also"></a>请参阅

[国际化](../c-runtime-library/internationalization.md)\
[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)
