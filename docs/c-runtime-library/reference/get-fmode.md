---
title: _get_fmode | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_fmode
- _get_fmode
dev_langs:
- C++
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a28909e5e848712305fb28e8ac4d46180f8948cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398297"
---
# <a name="getfmode"></a>_get_fmode

获取文件 I/O 操作的默认文件转换模式。

## <a name="syntax"></a>语法

```C
errno_t _get_fmode( 
   int * pmode 
);
```

### <a name="parameters"></a>参数

*pmode*<br/>
指向与当前的默认模式填充的整数的指针： **_O_TEXT**或 **_O_BINARY**。

## <a name="return-value"></a>返回值

如果成功，则返回零；如果失败，则返回错误代码。 如果*pmode*是**NULL**中, 所述，将调用无效参数处理程序[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**和该函数将返回**EINVAL**。

## <a name="remarks"></a>备注

函数获取 [_fmode](../../c-runtime-library/fmode.md) 全局变量的值。 此变量指定默认文件转换模式为底层和流文件 I/O 操作，如 **_open**， **_pipe**， **fopen**，和[freopen](freopen-wfreopen.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_set_fmode](set-fmode.md) 中的示例。

## <a name="see-also"></a>请参阅

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
