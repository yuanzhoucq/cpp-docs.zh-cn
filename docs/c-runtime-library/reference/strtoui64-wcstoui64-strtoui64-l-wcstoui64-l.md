---
title: _strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l
ms.date: 4/2/2020
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
- _o__strtoui64
- _o__strtoui64_l
- _o__wcstoui64
- _o__wcstoui64_l
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
ms.openlocfilehash: f3c5631a34c35ed5f5b74e15dfc4225224215b89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365467"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l

将字符串转换为未签名**的__int64**值。

## <a name="syntax"></a>语法

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*strSource*<br/>
要转换的 null 终止的字符串。

*端点*<br/>
指向停止扫描的字符的指针。

*base*<br/>
要使用的基数。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_strtoui64**返回字符串*strSource*中表示的值，除非表示形式将导致溢出，在这种情况下，它将**返回_UI64_MAX**。 如果无法执行转换 **，_strtoui64**返回 0。

**_UI64_MAX**在"限制"中定义。H。

如果*strSource*为**NULL**或*基值*为非零，并且小于 2 或大于 36，**则 errno**设置为**EINVAL**。

有关这些代码和其他返回代码的详细信息[，请参阅_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>备注

**_strtoui64**函数将*strSource*转换为**未签名****的__int64**。 **_wcstoui64**是一个宽字符版本的 **_strtoui64;** 其*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

这两个函数停止读取字符串*strSource*的第一个字符，他们无法识别为数字的一部分。 这可能是终止空字符，也可以是第一个数字字符大于或等于*基*。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

当前区域**设置LC_NUMERIC类别**设置决定了*strSource*中半径字符的识别;有关详细信息，请参阅[设置区域设置](setlocale-wsetlocale.md)。 没有_l后缀的函数使用当前区域设置;**_strtoui64_l**和 **_wcstoui64_l**与没有 **_l**后缀的相应函数相同，只不过它们使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*端点*不是**NULL，** 则指向停止扫描的字符的指针存储在*端点指向*的位置。 如果无法执行转换（未找到有效数字或指定了无效的基），*则 strSource*的值存储在*endptr*指向的位置。

**_strtoui64**希望*strSource*指向以下形式的字符串：

> [*空白 ]*[**+** &#124; **-**][**0** ] **x** &#124; **x** [*]* 数字&#124;*字母**

*空白*可以由忽略的空格和制表符组成。 *数字*是一个或多个十进制数字。 *字母*是一个或多个字母"a"到"z"（或"A"到"Z"）。 不符合此形式的第一个字符停止扫描。 如果*基数*介于 2 和 36 之间，则用作数字的基数。 如果*基为*0，*则 strSource*指向的字符串的初始字符用于确定基。 如果第一个字符为 0，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果*基为*0，并且扫描的第一个字符为"0"，则假定八进制整数，并且"8"或"9"字符将停止扫描。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
