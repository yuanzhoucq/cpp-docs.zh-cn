---
title: _CrtDoForAllClientObjects | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs:
- C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 378ef3c6218d1f57cd1d817d8895b3ff8b081ecb
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105336"
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

应用程序提供的函数调用的所有 **_CLIENT_BLOCK**堆 （仅限调试版本） 中的类型。

## <a name="syntax"></a>语法

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>参数

*pfn*<br/>
指向应用程序提供的函数回调函数的指针。 此函数的第一个参数指向数据。 第二个参数是传递给调用的上下文指针 **_CrtDoForAllClientObjects**。

*context*<br/>
指向要传递给应用程序提供的函数的应用程序提供的上下文的指针。

## <a name="remarks"></a>备注

**_CrtDoForAllClientObjects**函数使用的内存块的堆链接的列表中搜索 **_CLIENT_BLOCK**找到块时使用此类型的应用程序提供的函数的类型和调用。 找到的块和*上下文*参数作为参数传递给应用程序提供的函数。 在调试期间，应用程序可以跟踪特定分配的组通过显式调用调试堆函数分配内存并指定向块分配 **_CLIENT_BLOCK**块类型。 然后，可以在泄露检测和内存状态报告期间，单独跟踪并分别报告这些块。

如果 **_CRTDBG_ALLOC_MEM_DF**位域[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)上，不启用标志 **_CrtDoForAllClientObjects**立即返回。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtDoForAllClientObjects**在预处理过程中删除。

有关详细信息 **_CLIENT_BLOCK**类型和其他调试函数如何它可以使用的请参阅[的调试堆块类型](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如果*pfn*是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)设置为**EINVAL**并返回该函数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>、\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库：** 仅限通用 C 运行时库的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
