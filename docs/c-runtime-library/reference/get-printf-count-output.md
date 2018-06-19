---
title: _get_printf_count_output | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 216df8d973f391db2b6114d9bbcb50dcf509c5b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398359"
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

指示是否[printf、 _printf_l、 wprintf、 _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-系列函数支持 **%n**格式。

## <a name="syntax"></a>语法

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>返回值

非零值; 如果 **%n**支持，则 0 如果 **%n**不支持。

## <a name="remarks"></a>备注

如果 **%n**不是支持 （默认值）、 遇到 **%n**任一的格式字符串中**printf**函数将调用无效参数处理程序中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果 **%n**启用支持 (请参阅[_set_printf_count_output](set-printf-count-output.md)) 然后 **%n**中所述的表现[格式规范语法： printf 和 wprintf函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_set_printf_count_output](set-printf-count-output.md) 示例。

## <a name="see-also"></a>请参阅

[_set_printf_count_output](set-printf-count-output.md)<br/>
