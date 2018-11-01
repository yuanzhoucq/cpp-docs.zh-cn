---
title: _set_error_mode
ms.date: 11/04/2016
apiname:
- _set_error_mode
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: 8c95ed45423b791a688f05ea30f48e188826a797
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502305"
---
# <a name="seterrormode"></a>_set_error_mode

修改 **__error_mode**来确定非默认位置，其中 C 运行时写入错误的可能终止程序的错误消息。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>参数

*mode_val*<br/>
错误消息的目标。

## <a name="return-value"></a>返回值

如果出现错误，则返回旧设置或 -1。

## <a name="remarks"></a>备注

通过设置的值来控制错误输出接收器 **__error_mode**。 例如，可以将输出定向到标准错误或使用**MessageBox** API。

*Mode_val*参数可以设置为以下值之一。

|参数|描述|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|错误接收器由 **__app_type**。|
|**_OUT_TO_STDERR**|错误接收器是一个标准错误。|
|**_OUT_TO_MSGBOX**|错误接收器是一个消息框。|
|**_REPORT_ERRMODE**|报告当前 **__error_mode**值。|

如果传入所列出的值之外的值，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则 **_set_error_mode**设置**errno**到**EINVAL**并返回-1。

用于时[断言](assert-macro-assert-wassert.md)， **_set_error_mode**在对话框中显示失败的语句，并可选择的选项**忽略**按钮，以便你可以继续运行程序。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_set_error_mode**|\<stdlib.h>|

## <a name="example"></a>示例

```C
// crt_set_error_mode.c
// compile with: /c
#include <stdlib.h>
#include <assert.h>

int main()
{
   _set_error_mode(_OUT_TO_STDERR);
   assert(2+2==5);
}
```

```Output
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>请参阅

[assert 宏、_assert、_wassert](assert-macro-assert-wassert.md)<br/>
