---
title: _get_current_locale
ms.date: 11/04/2016
api_name:
- _get_current_locale
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_current_locale
- __get_current_locale
- _get_current_locale
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
ms.openlocfilehash: a17e730b350eaf88cf1c51502fda3df5ae30f611
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956089"
---
# <a name="_get_current_locale"></a>_get_current_locale

获取表示当前区域设置的区域设置对象。

## <a name="syntax"></a>语法

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>返回值

表示当前区域设置的区域设置对象。

## <a name="remarks"></a>备注

**_Get_current_locale**函数获取线程的当前设置的区域设置，并返回表示该区域设置的区域设置对象。

此函数的先前名称 **__get_current_locale** （具有两个前导下划线）已弃用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_current_locale**|\<locale.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
