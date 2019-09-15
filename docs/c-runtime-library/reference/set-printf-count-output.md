---
title: _set_printf_count_output
ms.date: 11/04/2016
api_name:
- _set_printf_count_output
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d53b4e4c56a69582a4eb517fa1a5c9e10cd7d2f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948423"
---
# <a name="_set_printf_count_output"></a>_set_printf_count_output

启用或禁用[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)系列函数中的 **% n**格式支持。

## <a name="syntax"></a>语法

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>参数

*enable*<br/>
若要启用 **% n**支持，则为非零值，0指示禁用 **% n**支持。

## <a name="property-valuereturn-value"></a>属性值/返回值

在调用此函数之前， **% n**的状态支持：如果启用了 **% n**支持，则为非零; 如果已禁用，则为0。

## <a name="remarks"></a>备注

出于安全考虑，默认情况下，在**printf**及其所有变体中禁用对 **% n**格式说明符的支持。 如果在**printf**格式规范中遇到 **% n** ，则默认行为是调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 使用非零参数调用 **_set_printf_count_output**将导致**printf**系列函数解释 **% n** ，如[格式规范语法： printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)中所述。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>请参阅

[_get_printf_count_output](get-printf-count-output.md)<br/>
