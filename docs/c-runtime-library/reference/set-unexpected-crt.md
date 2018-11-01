---
title: set_unexpected (CRT)
ms.date: 11/04/2016
apiname:
- set_unexpected
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
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: 6c38421e447ca7b3f263148f51f0ade5c59e2804
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484222"
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

安装要由 **unexpected** 调用的自身的终止函数。

## <a name="syntax"></a>语法

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>参数

*unexpFunction*<br/>
编写要替换的函数指针**意外**函数。

## <a name="return-value"></a>返回值

返回由注册的上一个终止函数的指针 **_set_unexpected** ，以便稍后能还原上一个函数。 如果已设置上一个函数，返回值可能用于还原默认行为;此值可能**NULL**。

## <a name="remarks"></a>备注

**Set_unexpected**函数安装*unexpFunction*由调用的函数作为**意外**。 **意外**不在当前 c + + 异常处理实现中使用。 **Unexpected_function** EH 中定义类型。为指向用户定义的意外函数，H *unexpFunction* ，它返回**void**。 您的自定义*unexpFunction*函数不应返回到其调用方。

```cpp
typedef void ( *unexpected_function )( );
```

默认情况下**意外**调用**终止**。 您可以更改此默认行为： 编写您自己的终止函数并调用**set_unexpected**与作为其参数函数的名称。 **意外**调用的最后一个函数的参数被当作**set_unexpected**。

与安装通过调用的自定义终止函数不同**set_terminate**，可以在引发异常*unexpFunction*。

在多线程环境中，单独为每个线程维护意外函数。 每个新线程都需要安装它自己的意外函数。 因此，每个线程都负责它自己的意外处理。

在当前的 Microsoft 实现的 c + + 异常处理**意外**调用**终止**默认情况下，永远不会调用异常处理运行时库。 没有特定于调用优势**意外**而非**终止**。

没有单个**set_unexpected**处理程序的所有动态链接的 Dll 或 Exe; 即使你调用**set_unexpected**可能由另一个替换您的处理程序，或要替换处理程序集另一个 DLL 或 EXE。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
