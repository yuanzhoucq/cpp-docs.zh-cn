---
title: _setmaxstdio | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 785fcc05c6b19086c14edc85983749894c867c18
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="setmaxstdio"></a>_setmaxstdio

设置在同时打开的文件数的最大**stdio**级别。

## <a name="syntax"></a>语法

```C
int _setmaxstdio(
   int newmax
);
```

### <a name="parameters"></a>参数

*newmax*<br/>
新最大同时打开的文件在数**stdio**级别。

## <a name="return-value"></a>返回值

返回*newmax*如果成功; 否则为-1。

如果*newmax*是小于 **_IOB_ENTRIES**或更高版本操作系统的无效参数处理程序中可用的句柄的最大数量调用中所述，然后[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将返回-1 并设置**errno**到**EINVAL**。

有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Setmaxstdio**函数更改可能在同时打开的文件数的最大值**stdio**级别。

相比早期版本，现在 C 运行时 I/O 在 Win32 平台上支持更多的打开文件。 2048 文件最多可以同时打开[lowio 级别](../../c-runtime-library/low-level-i-o.md)(即，打开和访问通过 **_open**，**阅读 （_r)**， **_write**、 I/O 函数系列，依此类推)。 512 文件最多可以同时打开[stdio 级别](../../c-runtime-library/stream-i-o.md)(即，打开和访问通过**fopen**， **fgetc**， **fputc**依次类推系列的函数)。 在 512 打开的文件的限制**stdio**级别可以增加到最大通过 2048 **_setmaxstdio**函数。

因为**stdio**-级别函数，如**fopen**，生成的顶部**lowio**函数，最大值为 2048 是数硬上限同时打开访问通过 C 运行时库的文件。

> [!NOTE]
> 此上限可能会超过特定 Win32 平台和配置所支持的文件数。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅[_getmaxstdio](getmaxstdio.md)有关的使用示例 **_setmaxstdio**。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
