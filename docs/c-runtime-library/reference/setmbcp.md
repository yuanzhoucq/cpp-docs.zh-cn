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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9a981c40b9e525ba1ffc1f2198f2b6a859fd9ac7
ms.sourcegitcommit: b51703a96ee35ee2376d5f0775b70f03ccbe6d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88086963"
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

*ansi*<br/>
独立于区域设置的多字节例程的新代码页设置。

## <a name="return-value"></a>返回值

如果已成功设置代码页，则返回 0。 如果为*代码*页提供了无效的代码页值，则返回-1，并且代码页设置不变。 如果内存分配失败，则将**errno**设置为**EINVAL** 。

## <a name="remarks"></a>备注

**_Setmbcp**函数指定新的多字节代码页。 默认情况下，运行时系统将多字节代码页自动设置为系统默认的 ANSI 代码页。 多字节代码页设置将影响所有独立于区域设置的多字节例程。 但是，可以指示 **_setmbcp**使用为当前区域设置定义的代码页 (请参阅下面列出的清单常量和关联的行为结果) 。 有关依赖于区域设置代码页，而不是多字节代码页的多字节例程的列表，请参阅[多字节字符序列解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。

*代码页*参数可设置为以下任意值：

- **_MB_CP_ANSI**使用在程序启动时从操作系统获取的 ANSI 代码页。

- **_MB_CP_LOCALE**使用从对[setlocale](setlocale-wsetlocale.md)的先前调用获取的当前区域设置的代码页。

- **_MB_CP_OEM**使用在程序启动时从操作系统获取的 OEM 代码页。

- **_MB_CP_SBCS**使用单字节代码页。 将代码页设置为 **_MB_CP_SBCS**时，例程（如[_ismbblead](ismbblead-ismbblead-l.md) ）始终返回 false。

- **_MB_CP_UTF8**使用 UTF-8。  将代码页设置为 **_MB_CP_UTF8**时，例程（如[_ismbblead](ismbblead-ismbblead-l.md) ）始终返回 false。

- 任何其他有效的代码页值，无论该值是 ANSI、OEM 还是其他操作系统支持的代码页 (除了 UTF-7 外，不支持) 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[_getmbcp](getmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
