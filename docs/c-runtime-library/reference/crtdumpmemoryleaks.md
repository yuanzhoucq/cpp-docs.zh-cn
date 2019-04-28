---
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
apiname:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
ms.openlocfilehash: baf4f8d8234ba744acda20541d37bbc3ed076678
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339450"
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

发生内存泄漏时，转储调试堆中的所有内存块（仅限调试版本）。

## <a name="syntax"></a>语法

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>返回值

**_CrtDumpMemoryLeaks**如果找到内存泄漏，则返回 TRUE。 否则，此函数返回 FALSE。

## <a name="remarks"></a>备注

**_CrtDumpMemoryLeaks**函数确定自程序开始执行以来是否发生了内存泄漏。 当发现泄漏时，以用户可读形式转储堆中所有对象的调试标头信息。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtDumpMemoryLeaks**在预处理过程中删除。

**_CrtDumpMemoryLeaks**频繁调用以验证是否已释放分配的应用程序的所有内存的程序执行结束时。 调用该函数会自动在程序终止时开启 **_CRTDBG_LEAK_CHECK_DF**位域[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)标志使用[_CrtSetDbgFlag](crtsetdbgflag.md)函数。

**_CrtDumpMemoryLeaks**调用[_CrtMemCheckpoint](crtmemcheckpoint.md)以获取堆的当前状态，然后扫描尚未释放的块的状态。 当遇到未释放的块时， **_CrtDumpMemoryLeaks**调用[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)到转储开始执行程序从堆中分配的所有对象的信息。

默认情况下，内部 C 运行时块 (**_CRT_BLOCK**) 未包含在内存转储操作。 [_CrtSetDbgFlag](crtsetdbgflag.md)函数可以用于开启 **_CRTDBG_CHECK_CRT_DF**位 **_crtDbgFlag**以将这些块包含在泄漏检测进程中。

有关详细信息，有关堆状态函数和 **_CrtMemState**结构，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用的示例 **_CrtDumpMemoryLeaks**，请参阅[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
