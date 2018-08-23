---
title: _get_current_locale | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_current_locale
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
- get_current_locale
- __get_current_locale
- _get_current_locale
dev_langs:
- C++
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c658d960953bea2890202bebe280d46dd3407d63
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396935"
---
# <a name="getcurrentlocale"></a>_get_current_locale

获取表示当前区域设置的区域设置对象。

## <a name="syntax"></a>语法

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>返回值

表示当前区域设置的区域设置对象。

## <a name="remarks"></a>备注

**_Get_current_locale**函数获取当前设置线程的区域设置，并返回一个表示该区域设置的区域设置对象。

此函数的以前名称 **__get_current_locale** （带两个前导下划线） 已弃用。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_get_current_locale**|\<locale.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
