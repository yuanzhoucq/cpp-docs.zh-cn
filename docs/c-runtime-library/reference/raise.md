---
title: raise | Microsoft 文档
ms.custom: ''
ms.date: 1/02/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- raise
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
- Raise
dev_langs:
- C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7b4c6bc2668089c4e6b813a03246e0690d1b4af
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="raise"></a>raise

将信号发送到正在执行的程序。

> [!NOTE]
> 不要使用此方法可以在测试或调试方案中关闭除 Microsoft 应用商店应用。 编程或 UI 方式关闭应用商店应用程序不允许根据[Microsoft 存储策略](http://go.microsoft.com/fwlink/?LinkId=865936)。 有关详细信息，请参阅[UWP 应用生命周期](http://go.microsoft.com/fwlink/p/?LinkId=865934)。

## <a name="syntax"></a>语法

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>参数

*sig*<br/>
要引发的信号。

## <a name="return-value"></a>返回值

如果成功，则 **raise** 返回 0。 否则，返回一个非零值。

## <a name="remarks"></a>备注

**raise** 函数将 *sig* 发送到正在执行的程序。 如果对 **signal** 的之前调用已经为 *sig* 安装了信号处理函数，则 **raise** 将执行该函数。 如果未安装处理程序函数，则执行与信号值 *sig* 相关联的默认操作，如下所示：

|Signal|含义|默认|
|------------|-------------|-------------|
|**SIGABRT**|异常终止|使用退出代码 3 终止调用程序|
|**SIGFPE**|浮点错误|终止调用程序|
|**SIGILL**|非法指令|终止调用程序|
|**SIGINT**|CTRL+C 中断|终止调用程序|
|**SIGSEGV**|非法存储区访问|终止调用程序|
|**SIGTERM**|发送到程序的终止请求|忽略信号|

如果参数不是以上指定的有效信号，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果未得到处理，该函数将设置**errno**到**EINVAL**并返回一个非零值。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**raise**|\<signal.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
