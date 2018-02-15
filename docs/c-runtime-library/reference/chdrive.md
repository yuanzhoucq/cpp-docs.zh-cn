---
title: "_chdrive | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1290f5a29ce2b6d80f98889fbb0fc5709cfa43e4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="chdrive"></a>_chdrive
更改当前工作驱动器。  
  
> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。  
  
## <a name="syntax"></a>语法  
  
```  
int _chdrive(   
   int drive   
);  
```  
  
#### <a name="parameters"></a>参数  
 `drive`  
 指定当前工作驱动器的 1 到 26 的整数（1=A，2=B 等）。  
  
## <a name="return-value"></a>返回值  
 如果已成功更改当前工作驱动器，则为零 (0)，否则为 -1。  
  
## <a name="remarks"></a>备注  
 如果 `drive` 不在 1 到 26 的范围内，则会调用无效的函数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则 **_chdrive** 函数将返回 -1，将 `errno` 设置为 `EACCES` 并且将 `_doserrno` 设置为 `ERROR_INVALID_DRIVE`。  
  
 **_chdrive** 函数不具备线程安全，因为它依赖 **SetCurrentDirectory** 函数，该函数本身不具备线程安全。 若要在多线程应用程序中安全地使用 **_chdrive**，必须提供自己的线程同步。 有关详细信息，请转到 [MSDN 库](http://go.microsoft.com/fwlink/p/?linkid=150542)，然后搜索 **SetCurrentDirectory**。  
  
 **_chdrive** 函数仅更改当前工作驱动器；**_chdir** 更改当前工作目录。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|**_chdrive**|\<direct.h>|  
  
 有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_getdrive](../../c-runtime-library/reference/getdrive.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [_chdir、_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getcwd、_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir、_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)