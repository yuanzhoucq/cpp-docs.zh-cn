---
title: _findclose
ms.date: 11/04/2016
apiname:
- _findclose
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
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: 29010f8a502d463eeb6ca98837a1b7dae9f5ae6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538107"
---
# <a name="findclose"></a>_findclose

关闭指定的搜索句柄并释放关联资源。

## <a name="syntax"></a>语法

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>参数

*句柄*<br/>
通过以前调用返回的搜索句柄 **_findfirst**。

## <a name="return-value"></a>返回值

如果成功， **_findclose**返回 0。 否则，它将返回-1，并设置**errno**到**ENOENT**，指示没有更多的匹配文件，找不到。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_findclose**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[系统调用](../../c-runtime-library/system-calls.md)<br/>
[文件名搜索函数](../../c-runtime-library/filename-search-functions.md)<br/>
