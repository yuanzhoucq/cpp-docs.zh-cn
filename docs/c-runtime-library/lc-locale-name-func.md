---
title: ___lc_locale_name_func
ms.date: 4/2/2020
api_name:
- ___lc_locale_name_func
- _o____lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: c48041c6c01e22c7771c0b5449de2cc8df1a2df0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912974"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

内部 CRT 函数。 检索线程的当前区域设置名称。

## <a name="syntax"></a>语法

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>返回值

指向包含线程的当前区域设置名称的字符串的指针。

## <a name="remarks"></a>备注

`___lc_locale_name_func` 是一个内部 CRT 函数，其他 CRT 函数可将其用于从 CRT 数据的线程本地存储中获取当前区域设置名称。 也可通过使用 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) 函数或 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 函数提供此信息。

内部 CRT 函数特定于实现且会根据每个发行版本发生更改。 不建议在代码中使用它们。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>另请参阅

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
