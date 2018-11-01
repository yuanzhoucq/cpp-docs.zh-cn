---
title: _CrtDbgBreak
ms.date: 11/04/2016
apiname:
- _CrtDbgBreak
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
- _CrtDbgBreak
- CrtDbgBreak
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
ms.openlocfilehash: 4cf64daaea3193f7cf6b3aaa0b1aab031f104704
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478295"
---
# <a name="crtdbgbreak"></a>_CrtDbgBreak

在特定代码行上设置断点。 （仅限调试模式。）

## <a name="syntax"></a>语法

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>返回值

没有返回值。

## <a name="remarks"></a>备注

**_CrtDbgBreak**函数调试断点上设置特定的代码行函数所在的位置。 此函数在调试模式下使用以及什么依赖于 **_DEBUG**之前未定义的。

有关使用其他具有挂钩功能的运行时函数和编写你自己的客户端定义挂钩函数的详细信息，请参阅[编写你自己的调试挂钩函数](/visualstudio/debugger/debug-hook-function-writing)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtDbgBreak**|\<CRTDBG.h>|

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[__debugbreak](../../intrinsics/debugbreak.md)<br/>
