---
title: strtoul、_strtoul_l、wcstoul、_wcstoul_l
ms.date: 4/2/2020
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
- _o__strtoul_l
- _o__wcstoul_l
- _o_strtoul
- _o_wcstoul
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
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: 60ae432fb11c5a29da2c4830c2a85305c6eaa46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365618"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul、_strtoul_l、wcstoul、_wcstoul_l

将字符串转换为无符号的长整数值。

## <a name="syntax"></a>语法

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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

**strtoul**返回转换的值（如果有）或**溢出时ULONG_MAX。** 如果无法执行转换 **，则 strtoul**返回 0。 **wcstoul**返回类似于**strtoul**的值。 对于这两个函数，如果发生溢出或下溢 **，errno**设置为**ERANGE。**

关于此代码以及其他返回代码的详细信息，请参阅 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>备注

每个函数都会将输入字符串*strSource*转换为**未签名****的长**。

**strtoul**停止读取字符串*strSource*的第一个字符，它不能识别为数字的一部分。 这可能是终止空字符，也可以是第一个数字字符大于或等于*基*。 区域设置**的LC_NUMERIC**类别设置决定了*strSource*中半径字符的识别;有关详细信息，请参阅[设置区域设置](setlocale-wsetlocale.md)。 **斯特图尔**和**wcstoul**使用当前区域设置;**_strtoul_l**和 **_wcstoul_l**是相同的，只是它们使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*端点*不是**NULL，** 则指向停止扫描的字符的指针存储在*端点指向*的位置。 如果无法执行转换（未找到有效数字或指定了无效的基），*则 strSource*的值存储在*endptr*指向的位置。

**wcstoul**是一个宽字符版本的**斯特图尔**;其*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**斯特图尔**期望*strSource*指向以下形式的字符串：

> [*空白 ]*[**+** &#124; **-**][**0** ] **x** &#124; **x** [*]* 数字&#124;*字母**

*空白*可以由忽略的空格和制表符组成。 *数字*是一个或多个十进制数字。 *字母*是一个或多个字母"a"到"z"（或"A"到"Z"）。 不符合此形式的第一个字符停止扫描。 如果*基数*介于 2 和 36 之间，则用作数字的基数。 如果*基为*0，*则 strSource*指向的字符串的初始字符用于确定基。 如果第一个字符为 0，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果*基为*0，并且扫描的第一个字符为"0"，则假定八进制整数，并且"8"或"9"字符将停止扫描。 **strtoul**允许加**+**（ ）**-** 或减 （ ） 符号前缀;前导减号表示返回值为否定。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [strtod](strtod-strtod-l-wcstod-wcstod-l.md) 的示例。

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
