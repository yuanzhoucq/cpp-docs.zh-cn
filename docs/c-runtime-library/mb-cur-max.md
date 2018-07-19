---
title: MB_CUR_MAX |Microsoft 文档
ms.custom: ''
ms.date: 10/18/2017
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- MB_CUR_MAX
dev_langs:
- C++
helpviewer_keywords:
- MB_CUR_MAX constant
ms.assetid: fab22609-c14d-4c19-991c-bd09ff30e604
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c9b290df51d631251811d1f8a92dff980304b24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390376"
---
# <a name="mbcurmax"></a>MB_CUR_MAX

一个指示当前区域设置的多字节字符中最大字节数的宏。

## <a name="syntax"></a>语法

`#include <stdlib.h>`

## <a name="remarks"></a>备注

上下文：ANSI 多字节字符和宽字符转换函数

`MB_CUR_MAX` 的值是当前区域设置的多字节字符中的最大字节数。

## <a name="see-also"></a>请参阅

[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
[___mb_cur_max_func、___mb_cur_max_l_func、__p___mb_cur_max、__mb_cur_max](../c-runtime-library/mb-cur-max-func-mb-cur-max-l-func-p-mb-cur-max-mb-cur-max.md)   
[标准类型](../c-runtime-library/standard-types.md)   
[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)   
[数据类型常量](../c-runtime-library/data-type-constants.md)   
[全局常量](../c-runtime-library/global-constants.md)