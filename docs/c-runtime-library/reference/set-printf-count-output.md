---
title: _set_printf_count_output | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_printf_count_output
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
- set_printf_count_output
- _set_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 783225412b01430d1043dafd4761cb7432eaa1d7
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108314"
---
# <a name="setprintfcountoutput"></a>_set_printf_count_output

启用或禁用的支持 **%n**设置中的格式[printf、 _printf_l、 wprintf、 _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-系列函数。

## <a name="syntax"></a>语法

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>参数

*enable*<br/>
非零值，以启用 **%n**支持，0 表示禁用 **%n**支持。

## <a name="property-valuereturn-value"></a>属性值/返回值

状态 **%n**之前调用此函数支持： 非零值; 如果 **%n**支持已启用，如果它已被禁用，则为 0。

## <a name="remarks"></a>备注

出于安全考虑，支持 **%n**格式说明符在默认情况下禁用**printf**及其变体。 如果 **%n**中遇到**printf**格式规范中，默认行为是调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 调用 **_set_printf_count_output**具有非零参数将导致**printf**-系列函数解释 **%n**中所述[格式规范语法： printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

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
