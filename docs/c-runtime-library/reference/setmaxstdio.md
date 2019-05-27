---
title: _setmaxstdio
ms.date: 05/21/2019
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
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 94b768d920ffd86a5bd762f8994244dda67fb15f
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174820"
---
# <a name="setmaxstdio"></a>_setmaxstdio

设置在流 I/O 级别同时打开的最大文件数。

## <a name="syntax"></a>语法

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>参数

*new_max*<br/>
在流 I/O 级别同时打开的新的最大文件数。

## <a name="return-value"></a>返回值

如果成功，返回 new_max；否则，返回 -1。

如果 new_max 小于 _IOB_ENTRIES 或大于操作系统中可用的句柄的最大数量，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 -1 并将 errno 设置为 EINVAL。

有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_setmaxstdio** 函数更改可在流 I/O 级别同时打开的文件数的最大值。

C 运行时 I/O 现在支持在[低 I/O 级别](../../c-runtime-library/low-level-i-o.md)同时打开最多 8,192 个文件。 此级别包括使用 I/O 函数的 _open、_read 和 _write 系列打开和访问的文件。 默认情况下，在[流 I/O 级别](../../c-runtime-library/stream-i-o.md)可以同时打开最多 512 个文件。 此级别包括使用函数的 fopen、fgetc 和 fputc 系列打开和访问的文件。 使用 _setmaxstdio 函数可以将在流 I/O 级别最多打开 512 个文件的限制增加到最多 8,192 个文件。

因为 fopen 等流 I/O 级别函数是基于低 I/O 级别函数生成的，8,192 的最大值是通过 C 运行时库访问的同时打开文件数的硬上限。

> [!NOTE]
> 此上限可能会超过特定 Win32 平台和配置所支持的文件数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_getmaxstdio](getmaxstdio.md)，获取使用 **_setmaxstdio** 的示例。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
