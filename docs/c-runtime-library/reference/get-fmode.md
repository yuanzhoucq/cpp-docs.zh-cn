---
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: 3e59e608f83874088b64d316c04053b94d8fbfdd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909854"
---
# <a name="_get_fmode"></a>_get_fmode

获取文件 I/O 操作的默认文件转换模式。

## <a name="syntax"></a>语法

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>参数

*pmode*<br/>
指向要用当前默认模式填充的整数的指针： **_O_TEXT**或 **_O_BINARY**。

## <a name="return-value"></a>返回值

如果成功，则返回零；如果失败，则返回错误代码。 如果*pmode*为**NULL**，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且函数将返回**EINVAL**。

## <a name="remarks"></a>备注

函数获取 [_fmode](../../c-runtime-library/fmode.md) 全局变量的值。 此变量为低级和流文件 i/o 操作指定默认的文件转换模式，如 **_open**、 **_pipe**、 **fopen**和[freopen](freopen-wfreopen.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_set_fmode](set-fmode.md) 中的示例。

## <a name="see-also"></a>另请参阅

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[文本和二进制模式文件 i/o](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
