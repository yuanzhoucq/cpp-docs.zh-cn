---
title: _setmbcp
ms.date: 11/04/2016
apiname:
- _setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: c1f4967baa5fda68a7df33bcd08935dca23fab16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532205"
---
# <a name="setmbcp"></a>_setmbcp

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

如果已成功设置代码页，则返回 0。 如果为提供无效的代码页值*代码页*，返回-1 和代码页设置保持不变。 集**errno**到**EINVAL**发生内存分配失败。

## <a name="remarks"></a>备注

**_Setmbcp**函数指定新的多字节代码页。 默认情况下，运行时系统将多字节代码页自动设置为系统默认的 ANSI 代码页。 多字节代码页设置将影响所有独立于区域设置的多字节例程。 但是，很可能会指示 **_setmbcp**使用为当前区域设置定义的代码页 （请参阅以下清单常量的列表和关联的行为结果）。 有关依赖于区域设置代码页，而不是多字节代码页的多字节例程的列表，请参阅[多字节字符序列解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。

多字节代码页还会通过以下运行时库例程来影响多字节字符处理：

||||
|-|-|-|
|[_exec 函数](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

此外，接收多字节字符的所有运行时库例程*argv*或*envp*程序自变量作为参数 (如 **_exec**和 **_spawn**系列) 来处理这些字符串根据多字节代码页。 因此，这些例程也会受到影响通过调用 **_setmbcp**更改多字节代码页。

*代码页*参数可以设置为以下值之一：

- **_MB_CP_ANSI**从在程序启动的操作系统使用 ANSI 代码页获得。

- **_MB_CP_LOCALE**使用当前区域设置的代码页从上一个调用中获取[setlocale](setlocale-wsetlocale.md)。

- **_MB_CP_OEM**从在程序启动的操作系统使用 OEM 代码页获得。

- **_MB_CP_SBCS**使用单字节代码页。 如果代码页设置为 **_MB_CP_SBCS**，例如日常[_ismbblead](ismbblead-ismbblead-l.md)始终返回 false。

- 任何其他有效的代码页值，而不考虑该值是否为 ANSI、OEM 或其他操作系统支持的代码页（除不受支持的 UTF-7 和 UTF-8 以外）。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_getmbcp](getmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
