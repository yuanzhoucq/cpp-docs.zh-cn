---
title: _pclose
ms.date: 4/2/2020
api_name:
- _pclose
- _o__pclose
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: c66a749d6aeb74fdc677b2d6088e1b5093f3570b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338525"
---
# <a name="_pclose"></a>_pclose

等待新命令处理器并关闭关联管道上的流。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>参数

*流*<br/>
将上一个调用的值返回 **_popen**。

## <a name="return-value"></a>返回值

返回终止命令处理器的退出状态，如果发生错误，返回 -1。 返回值的格式与 **_cwait**的格式相同，但交换低阶和高阶字节除外。 如果流为**NULL** **NULL，_pclose**将**errno**设置到**EINVAL**并返回 -1。

有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_pclose**函数查找由关联的 **_popen**调用启动的命令处理器 （Cmd.exe） 的进程 ID，在新命令处理器上执行[_cwait](cwait.md)调用，并关闭关联管道上的流。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen、_wpopen](popen-wpopen.md)<br/>
