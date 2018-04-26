---
title: _CrtCheckMemory | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
dev_langs:
- C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 18d1a51012a0950af2fe77cba4d8ecd0b1c89f90
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory

确认在调试堆中分配的内存块的完整性（仅限调试版）。

## <a name="syntax"></a>语法

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>返回值

如果成功， **_CrtCheckMemory**返回 TRUE; 否则为此函数返回 FALSE。

## <a name="remarks"></a>备注

**_CrtCheckMemory**函数验证通过验证基础基堆，并检查每个内存块由调试堆管理器分配的内存。 如果基础基堆、 调试标头信息或覆盖缓冲区中遇到的错误或内存不一致，则 **_CrtCheckMemory**描述错误条件的信息与生成调试报告。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtCheckMemory**在预处理过程中删除。

行为 **_CrtCheckMemory**可以通过设置的位域控制[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)标志使用[_CrtSetDbgFlag](crtsetdbgflag.md)函数。 打开 **_CRTDBG_CHECK_ALWAYS_DF**位字段 ON 导致 **_CrtCheckMemory**每次请求内存分配操作时调用。 尽管此方法减慢了执行速度，但它对快速捕获错误很有用。 打开 **_CRTDBG_ALLOC_MEM_DF**位字段 OFF 原因 **_CrtCheckMemory**不验证堆并立即返回**TRUE**。

因为此函数返回 **TRUE** 或 **FALSE**，因此可将它传递到其中一个 [_ASSERT](assert-asserte-assert-expr-macros.md) 宏，以创建一种简单的调试错误处理机制。 在堆中检测到损坏时，下面的示例将导致断言失败：

```C
_ASSERTE( _CrtCheckMemory( ) );
```

详细了解如何 **_CrtCheckMemory**可以与其他调试函数一起使用，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关内存管理和调试堆的概述，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用的示例 **_CrtCheckMemory**，请参阅[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
