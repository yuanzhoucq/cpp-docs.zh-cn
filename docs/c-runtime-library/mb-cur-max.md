---
title: MB_CUR_MAX
ms.date: 10/18/2017
f1_keywords:
- MB_CUR_MAX
helpviewer_keywords:
- MB_CUR_MAX constant
ms.assetid: fab22609-c14d-4c19-991c-bd09ff30e604
ms.openlocfilehash: 640821f920021435f8e79d9316d5eb0836c5f145
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220122"
---
# <a name="mbcurmax"></a>MB_CUR_MAX

一个指示当前区域设置的多字节字符中最大字节数的宏。

## <a name="syntax"></a>语法

```
#include <stdlib.h>
```

## <a name="remarks"></a>备注

上下文：ANSI 多字节字符和宽字符转换函数

`MB_CUR_MAX` 的值是当前区域设置的多字节字符中的最大字节数。

## <a name="see-also"></a>请参阅

[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)<br/>
[&#95;&#95;&#95;mb_cur_max_func、&#95;&#95;&#95;mb_cur_max_l_func、&#95;&#95;p&#95;&#95;&#95;mb_cur_max、&#95;&#95;mb_cur_max](../c-runtime-library/mb-cur-max-func-mb-cur-max-l-func-p-mb-cur-max-mb-cur-max.md)<br/>
[标准类型](../c-runtime-library/standard-types.md)<br/>
[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)<br/>
[数据类型常量](../c-runtime-library/data-type-constants.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)
