---
title: _chdrive
ms.date: 11/04/2016
apiname:
- _chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 963b7b7b40b632981abfc1529beb9c48a5b991ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602301"
---
# <a name="chdrive"></a>_chdrive

更改当前工作驱动器。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>参数

*驱动器*<br/>
指定当前工作驱动器的 1 到 26 的整数（1=A，2=B 等）。

## <a name="return-value"></a>返回值

如果已成功更改当前工作驱动器，则为零 (0)，否则为 -1。

## <a name="remarks"></a>备注

如果*驱动器*是不在 1 到 26 的范围，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则 **_chdrive**函数返回-1， **errno**设置为**EACCES**，以及 **_doserrno**设置为**ERROR_INVALID_DRIVE**。

**_chdrive** 函数不具备线程安全，因为它依赖 **SetCurrentDirectory** 函数，该函数本身不具备线程安全。 若要在多线程应用程序中安全地使用 **_chdrive**，必须提供自己的线程同步。 有关详细信息，请参阅[SetCurrentDirectory](/windows/desktop/api/winbase/nf-winbase-setcurrentdirectory)。

**_chdrive** 函数仅更改当前工作驱动器；**_chdir** 更改当前工作目录。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_getdrive](getdrive.md) 的示例。

## <a name="see-also"></a>请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
