---
title: _CrtSetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtSetDumpClient
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: f739f86a8410c66135704d61944d122a38c196a5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938562"
---
# <a name="_crtsetdumpclient"></a>_CrtSetDumpClient

安装应用程序定义的函数以转储 **_CLIENT_BLOCK**类型的内存块（仅限调试版本）。

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

**_CrtSetDumpClient**函数允许应用程序将其自己的函数挂钩到将存储在 **_CLIENT_BLOCK**内存块中的对象转储到 C 运行时调试内存转储进程。 因此，每当调试转储函数（如[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)或[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) ）转储 **_CLIENT_BLOCK**内存块时，也会调用该应用程序的转储函数。 **_CrtSetDumpClient**为应用程序提供了一种简单的方法来检测内存泄漏，并验证或报告存储在 **_CLIENT_BLOCK**块中的数据的内容。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtSetDumpClient**的调用。

**_CrtSetDumpClient**函数安装在*dumpClient*中指定的应用程序定义的新转储函数并返回以前定义的转储函数。 客户端块转储函数示例如下：

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*UserPortion*参数是一个指针，指向内存块的用户数据部分的开头，*区块*指定分配的内存块的大小（以字节为单位）。 客户端块转储函数必须返回**void**。 传递给 **_CrtSetDumpClient**的客户端转储函数的指针的类型为 **_CRT_DUMP_CLIENT**，如 crtdbg.h 中所定义：

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

有关在 **_CLIENT_BLOCK**类型内存块上操作的函数的详细信息，请参阅[CLIENT BLOCK 挂钩函数](/visualstudio/debugger/client-block-hook-functions)。 [_CrtReportBlockType](crtreportblocktype.md) 函数可用于返回有关块类型和子类型的信息。

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
