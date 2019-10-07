---
title: puts、_putws
ms.date: 11/04/2016
api_name:
- _putws
- puts
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
- _putts
- _putws
- puts
helpviewer_keywords:
- strings [C++], writing
- _putts function
- standard output, writing to
- putws function
- puts function
- putts function
- _putws function
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
ms.openlocfilehash: 1cd38678b321853cb229d86f9554bb76efbc84d6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949803"
---
# <a name="puts-_putws"></a>puts、_putws

将字符串写入 **stdout**。

## <a name="syntax"></a>语法

```C
int puts(
   const char *str
);
int _putws(
   const wchar_t *str
);
```

### <a name="parameters"></a>参数

*str*<br/>
输出字符串。

## <a name="return-value"></a>返回值

如果成功，则返回一个非负值。 如果**put 失败，则**返回**EOF**;如果 **_putws**失败，则返回**WEOF**。 如果*str*为空指针，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则函数将**errno**设置为**EINVAL** ，并返回**EOF**或**WEOF**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

Put**函数将** *str*写入标准输出流**stdout**，将字符串的终止 null 字符（"\ 0"）替换为输出流中的换行符（"\n"）。

**_putws**是的宽字符**版本;** 如果在 ANSI 模式下打开流，则这两个函数的行为相同。 put**当前不支持**到 UNICODE 流中的输出。

**_putwch**使用当前控制台区域设置写入 Unicode 字符。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_putts**|**puts**|**puts**|**_putws**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**puts**|\<stdio.h>|
|**_putws**|\<stdio.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 与控制台、 **stdin**、 **stdout**和**stderr**关联的标准流句柄必须重定向, 然后 C 运行时函数才能在 UWP 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_puts.c
// This program uses puts to write a string to stdout.

#include <stdio.h>

int main( void )
{
   puts( "Hello world from puts!" );
}
```

### <a name="output"></a>Output

```Output
Hello world from puts!
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputs、fputws](fputs-fputws.md)<br/>
[fgets、fgetws](fgets-fgetws.md)<br/>
