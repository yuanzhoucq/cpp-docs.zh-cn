---
title: _set_app_type
ms.date: 11/04/2016
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: f12e409355fcd10ece474103109286925b1f3a8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569814"
---
# <a name="setapptype"></a>_set_app_type

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

|“值”|描述|
|----------------|-----------------|
|_crt_unknown_app|未知应用程序类型。|
|_crt_console_app|控制台（命令行）应用程序。|
|_crt_gui_app|GUI (Windows) 应用程序。|

## <a name="remarks"></a>备注

通常情况下，不需要调用此函数。 它是在应用中调用 `main` 前执行的 C 运行时启动代码的一部分。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|_set_app_type|process.h|

