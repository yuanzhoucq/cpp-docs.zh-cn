---
title: _getmbcp
ms.date: 11/04/2016
apiname:
- _getmbcp
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
- _getmbcp
- getmbcp
helpviewer_keywords:
- code pages, determining current
- _getmbcp function
- getmbcp function
ms.assetid: 2db202d4-5c3d-4871-a0b8-ceb0b79ee7bb
ms.openlocfilehash: 4cea84fc771a1d847814d002294391256efae57b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620449"
---
# <a name="getmbcp"></a>_getmbcp

检索当前代码页。

## <a name="syntax"></a>语法

```C
int _getmbcp( void );
```

## <a name="return-value"></a>返回值

返回当前多字节代码页。 返回值为 0 表示单字节代码页正在使用中。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_getmbcp**|\<mbctype.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_setmbcp](setmbcp.md)<br/>
