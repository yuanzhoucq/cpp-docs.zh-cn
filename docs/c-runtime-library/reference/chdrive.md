---
title: _chdrive
ms.date: 4/2/2020
api_name:
- _chdrive
- _o__chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 0c19fefcf6a766842ee2e25cbe6bdb61bbf48e7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333349"
---
# <a name="_chdrive"></a>_chdrive

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

*驱动*<br/>
指定当前工作驱动器的 1 到 26 的整数（1=A，2=B 等）。

## <a name="return-value"></a>返回值

如果已成功更改当前工作驱动器，则为零 (0)，否则为 -1。

## <a name="remarks"></a>备注

如果*驱动器*不在 1 到 26 的范围内，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行 **，_chdrive**函数将返回 -1，errno 设置为**EACCES，_doserrno**设置为 **_doserrno****ERROR_INVALID_DRIVE**。 **errno**

**_chdrive** 函数不具备线程安全，因为它依赖 **SetCurrentDirectory** 函数，该函数本身不具备线程安全。 若要在多线程应用程序中安全地使用 **_chdrive**，必须提供自己的线程同步。 有关详细信息，请参阅[设置当前目录](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)。

**_chdrive** 函数仅更改当前工作驱动器；**_chdir** 更改当前工作目录。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_getdrive](getdrive.md) 的示例。

## <a name="see-also"></a>另请参阅

[目录控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
