---
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 2b78b7205b1e5dda7ac7062747c6dd1065ed1c94
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919917"
---
# <a name="_set_app_type"></a>_set_app_type

在启动时使用的内部函数告知 CRT，应用属于控制台应用程序还是 GUI 应用。

## <a name="syntax"></a>语法

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>参数

*appType*<br/>
表示应用程序类型的值。 可能的值为：

|值|说明|
|----------------|-----------------|
|_crt_unknown_app|未知应用程序类型。|
|_crt_console_app|控制台（命令行）应用程序。|
|_crt_gui_app|GUI (Windows) 应用程序。|

## <a name="remarks"></a>备注

通常情况下，不需要调用此函数。 它是在应用中调用 `main` 前执行的 C 运行时启动代码的一部分。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|_set_app_type|process.h|
