---
title: _CrtCheckMemory
ms.date: 11/04/2016
api_name:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: 7e458825a81b7032310458ccda52d9299e126a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938865"
---
# <a name="_crtcheckmemory"></a>_CrtCheckMemory

确认在调试堆中分配的内存块的完整性（仅限调试版）。

## <a name="syntax"></a>语法

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>返回值

如果成功，则 **_CrtCheckMemory**返回 TRUE;否则，该函数返回 FALSE。

## <a name="remarks"></a>备注

**_CrtCheckMemory**函数通过验证基础基堆并检查每个内存块来验证由调试堆管理器分配的内存。 如果在基础基堆中遇到错误或内存不一致，则 **_CrtCheckMemory**会生成一个调试报告，其中包含描述错误条件的信息。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtCheckMemory**的调用。

可以通过使用[_CrtSetDbgFlag](crtsetdbgflag.md)函数设置[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)标志的位域，来控制 **_CrtCheckMemory**的行为。 将 **_CRTDBG_CHECK_ALWAYS_DF**位域转换为时，每次请求内存分配操作时都会调用 **_CrtCheckMemory**中的结果。 尽管此方法减慢了执行速度，但它对快速捕获错误很有用。 将 **_CRTDBG_ALLOC_MEM_DF**位字段关闭会导致 **_CrtCheckMemory**不验证堆并立即返回**TRUE**。

因为此函数返回 **TRUE** 或 **FALSE**，因此可将它传递到其中一个 [_ASSERT](assert-asserte-assert-expr-macros.md) 宏，以创建一种简单的调试错误处理机制。 在堆中检测到损坏时，下面的示例将导致断言失败：

```C
_ASSERTE( _CrtCheckMemory( ) );
```

有关 **_CrtCheckMemory**如何与其他调试函数结合使用的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关内存管理和调试堆的概述，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用 **_CrtCheckMemory**的示例，请参阅[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
