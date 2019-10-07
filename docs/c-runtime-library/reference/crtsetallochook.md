---
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: 303f682b54abc5e44cb7fdd4c89012dd9913288b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938488"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

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

返回以前定义的分配挂钩函数，如果*allocHook*为**null**，则返回**null** 。

## <a name="remarks"></a>备注

**_CrtSetAllocHook**允许应用程序将其自己的分配函数挂钩到 C 运行时调试库内存分配进程。 因此，每次调用调试分配函数以分配、重新分配或释放内存块时都会触发对应用程序挂钩函数的调用。 **_CrtSetAllocHook**为应用程序提供了一种简单的方法来测试应用程序如何处理内存不足的情况、检查分配模式的能力，以及记录分配信息以供以后分析的机会。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtSetAllocHook**的调用。

**_CrtSetAllocHook**函数安装在*allocHook*中指定的新的客户端定义的分配函数，并返回之前定义的挂钩函数。 以下示例演示了客户端定义的分配挂钩如何构建原型：

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**AllocType**参数指定触发对分配的挂钩函数的调用的分配操作类型（ **_HOOK_ALLOC**、 **_HOOK_REALLOC**和 **_HOOK_FREE**）。 当触发分配类型为 **_HOOK_FREE**时， *userData*是指向要释放的内存块的用户数据部分的指针。 但是，当触发分配类型为 **_HOOK_ALLOC**或 **_HOOK_REALLOC**时， *userData*为**NULL** ，因为尚未分配内存块。

*大小*指定内存块的大小（以字节为单位）， *blockType*指示内存块的类型， *requestNumber*是内存块的对象分配序号，如果可用， *filename*和**lineNumber**指定启动触发分配操作的源文件名和行号。

挂钩函数处理完成后，必须返回一个布尔值，该值将告诉主 C 运行时分配进程如何继续。 如果挂钩函数想要主分配过程继续进行，就好像从未调用过挂钩函数一样，则挂钩函数应返回**TRUE**。 这将导致执行原始触发分配操作。 使用该实现，挂钩函数可以收集和保存分配信息以用于以后分析，而不会干扰调试堆的当前分配操作或状态。

如果挂钩函数想要主分配进程继续执行，就像调用触发分配操作并失败一样，则挂钩函数应返回**FALSE**。 使用这个实现，挂钩函数可以模拟大范围的内存条件和调试堆状态，以测试应用程序如何处理每种情况。

若要清除挂钩函数，请将**NULL**传递给 **_CrtSetAllocHook**。

有关 **_CrtSetAllocHook**如何与其他内存管理函数一起使用的详细信息，或者如何编写您自己的客户端定义的挂钩函数，请参阅[编写调试挂钩函数](/visualstudio/debugger/debug-hook-function-writing)。

> [!NOTE]
> **/Clr： pure**不支持 **_CrtSetAllocHook** 。 **/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，并在 visual studio 2017 中被删除。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用 **_CrtSetAllocHook**的示例，请参阅[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
