---
title: _pclose | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _pclose
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
- _pclose
- pclose
dev_langs:
- C++
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01e58c23bc91e8819abb3cd24f1ed01ee161ff8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401771"
---
# <a name="pclose"></a>_pclose

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
从调用返回值 **_popen**。

## <a name="return-value"></a>返回值

如果发生错误，则返回终止的命令处理器，则为-1 的退出状态。 返回值的格式是，对于相同 **_cwait**，只是交换的低序位和高序位字节。 如果流是**NULL**， **_pclose**设置**errno**到**EINVAL**并返回-1。

有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Pclose**函数查找命令处理器 (Cmd.exe) 启动由关联的进程 ID **_popen**调用，将执行[_cwait](cwait.md)调用新的命令处理器，并关闭关联的管道流。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen、_wpopen](popen-wpopen.md)<br/>
