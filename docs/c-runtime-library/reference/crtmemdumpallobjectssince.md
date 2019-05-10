---
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: 7de0ee9ff166af6336a8d14aa0dbd07dbd7d23fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347452"
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

从程序开始执行或从指定的堆状态转储堆中对象的信息（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>参数

*state*<br/>
指向开始从其转储的堆状态的指针，或 **NULL**。

## <a name="remarks"></a>备注

**_CrtMemDumpAllObjectsSince**函数转储调试标头信息的用户可读的窗体中的堆中分配的对象。 应用程序可以使用转储信息来跟踪分配并检测内存问题。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtMemDumpAllObjectsSince**在预处理过程中删除。

**_CrtMemDumpAllObjectsSince**使用的值*状态*参数，以确定启动转储操作的位置。 若要开始从指定的堆状态转储*状态*参数必须是指向指针 **_CrtMemState**由填充中的结构[_CrtMemCheckpoint](crtmemcheckpoint.md)之前 **_CrtMemDumpAllObjectsSince**调用。 当*状态*是**NULL**，该函数即开始从一开始程序执行的转储。

如果应用程序已安装了转储挂钩函数通过调用[_CrtSetDumpClient](crtsetdumpclient.md)，然后每次 **_CrtMemDumpAllObjectsSince**有关转储信息 **_CLIENT_BLOCK**类型的块，它将调用应用程序提供的转储函数。 默认情况下，内部 C 运行时块 (**_CRT_BLOCK**) 未包含在内存转储操作。 [_CrtSetDbgFlag](crtsetdbgflag.md)函数可以用于开启 **_CRTDBG_CHECK_CRT_DF**位 **_crtDbgFlag**以将这些块包含。 此外，标记为已释放或已忽略的块（**_FREE_BLOCK**、**_IGNORE_BLOCK**）不包括在内存转储中。

有关详细信息，有关堆状态函数和 **_CrtMemState**结构，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用的示例 **_CrtMemDumpAllObjectsSince**，请参阅[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
