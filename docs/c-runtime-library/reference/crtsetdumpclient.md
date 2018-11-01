---
title: _CrtSetDumpClient
ms.date: 11/04/2016
apiname:
- _CrtSetDumpClient
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
apitype: DLLExport
f1_keywords:
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: 09f319f6298dbec6b229b2923bd86fc9b50314de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470741"
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

安装的应用程序定义的函数来转储 **_CLIENT_BLOCK**类型内存块 （仅限调试版本）。

## <a name="syntax"></a>语法

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>参数

*dumpClient*<br/>
将新的客户端定义的内存转储函数挂钩到 C 运行时调试内存转储进程。

## <a name="return-value"></a>返回值

返回之前定义的客户端块转储函数。

## <a name="remarks"></a>备注

**_CrtSetDumpClient**函数允许应用程序将挂钩其自己的函数对象中存储的转储 **_CLIENT_BLOCK**到 C 运行时的内存块调试内存转储进程。 因此，每次调试转储函数如[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)或[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)转储 **_CLIENT_BLOCK**内存块，该应用程序同时也会调用转储函数。 **_CrtSetDumpClient**应用程序提供了一种简单方法用于检测内存泄漏以及验证或报告中存储的数据内容 **_CLIENT_BLOCK**块。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtSetDumpClient**在预处理过程中删除。

**_CrtSetDumpClient**函数安装中指定的新应用程序定义的转储函数*dumpClient*并返回之前定义的转储函数。 客户端块转储函数示例如下：

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*UserPortion*参数是指向内存块的用户数据部分的开头并*blockSize*指定已分配的内存大小的块以字节为单位。 客户端块转储函数必须返回**void**。 指向传递给客户端转储函数的指针 **_CrtSetDumpClient**属于类型 **_CRT_DUMP_CLIENT**，如 Crtdbg.h 中定义：

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

有关函数进行操作的详细信息 **_CLIENT_BLOCK**类型的内存块，请参阅[客户端块挂钩函数](/visualstudio/debugger/client-block-hook-functions)。 [_CrtReportBlockType](crtreportblocktype.md) 函数可用于返回有关块类型和子类型的信息。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
