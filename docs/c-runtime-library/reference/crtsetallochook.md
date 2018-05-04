---
title: _CrtSetAllocHook | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d86072ceb41b966adfca298152b6209450aace3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook

通过挂钩到 C 运行时调试内存分配进程安装客户端定义的分配函数（仅限调试版本）。

## <a name="syntax"></a>语法

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>参数

*allocHook*<br/>
将新的客户端定义的分配函数挂钩到 C 运行时调试内存分配进程。

## <a name="return-value"></a>返回值

返回以前定义的分配挂钩函数，或**NULL**如果*allocHook*是**NULL**。

## <a name="remarks"></a>备注

**_CrtSetAllocHook**允许应用程序挂钩到 C 运行时调试库内存分配进程的其自己的分配函数。 因此，每次调用调试分配函数以分配、重新分配或释放内存块时都会触发对应用程序挂钩函数的调用。 **_CrtSetAllocHook**向应用程序提供了一个简单方法测试应用程序如何处理内存不足情况，可以检查分配模式，并有机会记录分配信息以更高版本分析。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtSetAllocHook**在预处理过程中删除。

**_CrtSetAllocHook**函数安装中指定的新客户端定义的分配函数*allocHook*并返回以前定义的挂钩函数。 以下示例演示了客户端定义的分配挂钩如何构建原型：

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**AllocType**参数指定分配操作的类型 (**_HOOK_ALLOC**， **_HOOK_REALLOC**，和 **_HOOK_FREE**)，触发对分配挂钩函数的调用。 当触发的分配类型是 **_HOOK_FREE**， *userData*是指向要被释放的内存块的用户数据部分的指针。 但是，当触发的分配类型是 **_HOOK_ALLOC**或 **_HOOK_REALLOC**， *userData*是**NULL**因为内存块尚未分配尚未。

*大小*指定的内存的大小以字节为单位，阻止*blockType*指示的一种内存块， *requestNumber*是对象分配序号的内存块，并且，如果可用， *filename*和**lineNumber**指定的源文件名和行号初始化之前触发分配操作的位置。

挂钩函数处理完成后，必须返回一个布尔值，该值将告诉主 C 运行时分配进程如何继续。 挂钩函数时想继续作为，如果从未被调用过挂钩函数，则应返回挂钩函数的主要分配过程**TRUE**。 这将导致执行原始触发分配操作。 使用该实现，挂钩函数可以收集和保存分配信息以用于以后分析，而不会干扰调试堆的当前分配操作或状态。

挂钩函数时想继续作为，如果已调用触发分配操作仍然失败，则挂钩函数应返回的主要分配过程**FALSE**。 使用这个实现，挂钩函数可以模拟大范围的内存条件和调试堆状态，以测试应用程序如何处理每种情况。

若要清除挂钩函数，请将传递**NULL**到 **_CrtSetAllocHook**。

详细了解如何 **_CrtSetAllocHook**可以与其他内存管理函数或编写你自己的客户端定义挂钩函数，请参阅使用[调试挂钩函数编写](/visualstudio/debugger/debug-hook-function-writing)。

> [!NOTE]
> **_CrtSetAllocHook**下不支持 **/clr: pure**。 **/Clr: pure**和 **/clr: safe** Visual Studio 2015 中弃用并删除在 Visual Studio 2017 编译器选项。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用的示例 **_CrtSetAllocHook**，请参阅[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
