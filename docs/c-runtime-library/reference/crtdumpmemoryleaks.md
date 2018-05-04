---
title: _CrtDumpMemoryLeaks | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68a187283eedadcd2f435b0900fde648a5010368
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

发生内存泄漏时，转储调试堆中的所有内存块（仅限调试版本）。

## <a name="syntax"></a>语法

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>返回值

**_CrtDumpMemoryLeaks**如果找到了内存泄漏，则返回 TRUE。 否则，此函数返回 FALSE。

## <a name="remarks"></a>备注

**_CrtDumpMemoryLeaks**函数将确定自程序开始执行以来是否发生了内存泄漏。 当发现泄漏时，以用户可读形式转储堆中所有对象的调试标头信息。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtDumpMemoryLeaks**在预处理过程中删除。

**_CrtDumpMemoryLeaks**程序执行以验证已释放所有内存分配由应用程序结束时经常会对其进行调用。 调用该函数可以自动在程序终止时通过打开 **_CRTDBG_LEAK_CHECK_DF**位域[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)标志使用[_CrtSetDbgFlag](crtsetdbgflag.md)函数。

**_CrtDumpMemoryLeaks**调用[_CrtMemCheckpoint](crtmemcheckpoint.md)获取堆的当前状态，然后扫描不释放的块的状态。 当遇到未释放的块时， **_CrtDumpMemoryLeaks**调用[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)程序开始执行从堆中分配的所有对象的转储信息。

默认情况下，内部 C 运行时块 (**_CRT_BLOCK**) 不包括在内存转储操作。 [_CrtSetDbgFlag](crtsetdbgflag.md)函数可用来打开 **_CRTDBG_CHECK_CRT_DF**位的 **_crtDbgFlag**要包含在泄漏检测过程中的这些块。

有关堆状态函数和 **_CrtMemState**结构，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用的示例 **_CrtDumpMemoryLeaks**，请参阅[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
