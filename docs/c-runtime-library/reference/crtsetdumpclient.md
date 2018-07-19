---
title: _CrtSetDumpClient | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d5fecc90b4b7259f1440a0a0d86277c769c4e16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397218"
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

安装要转储的应用程序定义的函数 **_CLIENT_BLOCK**键入内存块 （仅限调试版本）。

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

**_CrtSetDumpClient**函数允许应用程序挂钩到转储对象存储在其自己的函数 **_CLIENT_BLOCK**到 C 运行时的内存块调试内存转储过程。 因此，每次调试转储函数如[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)或[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)转储 **_CLIENT_BLOCK**内存块、 应用程序的以及调用转储函数。 **_CrtSetDumpClient**向应用程序提供了一种简单方法为检测内存泄漏和验证或报告中存储的数据的内容 **_CLIENT_BLOCK**块。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtSetDumpClient**在预处理过程中删除。

**_CrtSetDumpClient**函数安装中指定的新应用程序定义转储函数*dumpClient*并返回以前定义的转储函数。 客户端块转储函数示例如下：

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*UserPortion*自变量是指向内存块的用户数据部分的开头和*blockSize*指定分配的内存的大小阻止以字节为单位。 客户端块转储函数必须返回**void**。 指向传递给客户端转储函数的指针 **_CrtSetDumpClient**属于类型 **_CRT_DUMP_CLIENT**，如 Crtdbg.h 中所定义：

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

有关函数进行操作的详细信息 **_CLIENT_BLOCK**类型内存块，请参阅[客户端块挂钩函数](/visualstudio/debugger/client-block-hook-functions)。 [_CrtReportBlockType](crtreportblocktype.md) 函数可用于返回有关块类型和子类型的信息。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
