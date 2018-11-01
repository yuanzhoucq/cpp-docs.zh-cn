---
title: _free_locale
ms.date: 11/04/2016
apiname:
- _free_locale
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
- __free_locale
- free_locale
- _free_locale
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
ms.openlocfilehash: 92dc8cd711087e8e797b484d6c7e3c6c3b031b5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537379"
---
# <a name="freelocale"></a>_free_locale

释放区域设置对象。

## <a name="syntax"></a>语法

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*locale*<br/>
要释放的区域设置对象。

## <a name="remarks"></a>备注

**_Free_locale**函数用于释放通过调用获取的区域设置对象 **_get_current_locale**或 **_create_locale**。

此函数的以前名称 **__free_locale** （带两个前导下划线） 已被弃用。

## <a name="requirements"></a>要求

|**例程**|必需的标头|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
