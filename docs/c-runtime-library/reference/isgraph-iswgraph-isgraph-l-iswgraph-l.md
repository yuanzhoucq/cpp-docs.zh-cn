---
title: isgraph、iswgraph、_isgraph_l、_iswgraph_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- isgraph
- iswgraph
- _iswgraph_l
- _isgraph_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _isgraph_l
- _iswgraph_l
- _ismbcgraph_l
- Isgraph
- _istgraph_l
- _istgraph
- iswgraph
dev_langs:
- C++
helpviewer_keywords:
- isgraph function
- _istgraph_l function
- istgraph function
- _isgraph_l function
- iswgraph function
- _iswgraph_l function
- _istgraph function
- _ismbcgraph_l function
ms.assetid: 531a5f34-4302-4d0a-8a4f-b7ea150ad941
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b60e022471bdfa7cbbddb6b5263f757438572a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="isgraph-iswgraph-isgraphl-iswgraphl"></a>isgraph、iswgraph、_isgraph_l、_iswgraph_l

确定整数是否表示图形字符。

## <a name="syntax"></a>语法

```C
int isgraph(
   int c
);
int iswgraph(
   wint_t c
);
int _isgraph_l(
   int c,
   _locale_t locale
);
int _iswgraph_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

每个这些例程返回非零如果*c*是的特定表示形式可打印字符的空间除外。 **isgraph**返回非零值，如果*c*是可打印字符的空间除外。 **iswgraph**返回非零值，如果*c*是可打印的宽字符的宽字符空间除外。 这些例程都返回 0 如果*c*不满足测试条件。

这些函数具有的版本 **_l**后缀其区域设置相关行为使用传入的区域设置而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

行为**isgraph**和 **_isgraph_l**如果是未定义*c*不是 EOF 或在 0 到 0xFF，非独占的范围。 使用 CRT 调试库时和*c*是不是一种这些值，函数引发的断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istgraph**|**isgraph**|[_ismbcgraph](ismbcgraph-functions.md)|**iswgraph**|
|**_istgraph_l**|**_isgraph_l**|[_ismbcgraph_l](ismbcgraph-functions.md)|**_iswgraph_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**isgraph**|\<ctype.h>|
|**iswgraph**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_isgraph_l**|\<ctype.h>|
|**_iswgraph_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
