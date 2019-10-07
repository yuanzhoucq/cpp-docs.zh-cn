---
title: _CrtDbgBreak
ms.date: 11/04/2016
api_name:
- _CrtDbgBreak
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
- _CrtDbgBreak
- CrtDbgBreak
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
ms.openlocfilehash: 9471b1a93abd9777c3a53c54c2517e59896d8160
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942586"
---
# <a name="_crtdbgbreak"></a>_CrtDbgBreak

在特定代码行上设置断点。 （仅限调试模式。）

## <a name="syntax"></a>语法

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>返回值

没有返回值。

## <a name="remarks"></a>备注

**_CrtDbgBreak**函数在函数所在的特定代码行上设置调试断点。 此函数仅在调试模式下使用，并且依赖于先前定义的 **_debug** 。

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
