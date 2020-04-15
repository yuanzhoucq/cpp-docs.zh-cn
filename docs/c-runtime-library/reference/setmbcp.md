---
title: _setmbcp
ms.date: 4/2/2020
api_name:
- _setmbcp
- _o__setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: 61086471c6194aaa8434d291647978bf891a8aea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337592"
---
# <a name="_setmbcp"></a>_setmbcp

设置新的多字节代码页。

## <a name="syntax"></a>语法

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>参数

*代码页*<br/>
独立于区域设置的多字节例程的新代码页设置。

## <a name="return-value"></a>返回值

如果已成功设置代码页，则返回 0。 如果为*代码页*提供了无效的代码页值，则返回 -1，并且代码页设置保持不变。 如果发生内存分配失败，则将**errno**设置到**EINVAL。**

## <a name="remarks"></a>备注

**_setmbcp**函数指定一个新的多字节代码页。 默认情况下，运行时系统将多字节代码页自动设置为系统默认的 ANSI 代码页。 多字节代码页设置将影响所有独立于区域设置的多字节例程。 但是，可以指示 **_setmbcp**使用为当前区域设置定义的代码页（请参阅以下清单常量和相关行为结果的列表）。 有关依赖于区域设置代码页，而不是多字节代码页的多字节例程的列表，请参阅[多字节字符序列解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。

多字节代码页还会通过以下运行时库例程来影响多字节字符处理：

||||
|-|-|-|
|[_exec 函数](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

此外，所有接收多字节字符*argv*或*envp*程序参数作为参数（如 **_exec**和 **_spawn**族）的运行时库例程都根据多字节代码页处理这些字符串。 因此，这些例程还受更改多字节代码页的 **_setmbcp**调用的影响。

*代码页*参数可以设置为以下任意值：

- **_MB_CP_ANSI**在程序启动时使用从操作系统获取的 ANSI 代码页。

- **_MB_CP_LOCALE**使用从上一个调用获取的当前区域设置码页[设置区域设置](setlocale-wsetlocale.md)。

- **_MB_CP_OEM**在程序启动时使用从操作系统获取的 OEM 代码页。

- **_MB_CP_SBCS**使用单字节代码页。 当代码页设置为 **_MB_CP_SBCS**时[，_ismbblead](ismbblead-ismbblead-l.md)等例程总是返回 false。

- **_MB_CP_UTF8**使用 UTF-8。  当代码页设置为 **_MB_CP_UTF8**时[，_ismbblead](ismbblead-ismbblead-l.md)等例程总是返回 false。

- 任何其他有效的代码页值，无论该值是 ANSI、OEM 还是其他操作系统支持的代码页（不支持的 UTF-7 除外）。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[_getmbcp](getmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
