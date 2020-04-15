---
title: set_terminate (CRT)
ms.date: 4/2/2020
api_name:
- set_terminate
- _o_set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 08ea5bb8c446fadac6a7bcf7ca172c5d14546776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332105"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

安装您自己的终止例程，由**终止**调用 。

## <a name="syntax"></a>语法

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>参数

*术语函数*<br/>
指向终止你编写的函数的指针。

## <a name="return-value"></a>返回值

返回指向**set_terminate**注册的前一个函数的指针，以便以后可以还原以前的函数。 如果未设置以前的函数，则返回值可用于还原默认行为;如果未设置以前的函数，则返回值可用于还原默认行为。此值可以是**NULL**。

## <a name="remarks"></a>备注

**set_terminate**函数将*术语函数*作为**终止**调用的函数。 **set_terminate**用于C++异常处理，并且可能在引发异常之前在程序中的任意点调用。 默认情况下**终止**呼叫[中止](abort.md)。 您可以通过编写自己的终止函数并将函数**的名称称为参数**set_terminate来更改此默认值。 **终止**调用作为参数给出的最后一个函数**set_terminate**。 执行任何所需的清理任务后，*术语函数*应退出程序。 如果它不退出（如果它返回到其调用方），则调用[中止](abort.md)。

在多线程环境中，终止单独为每个线程维护的函数。 每个新线程都需要安装自己的终止函数。 因此，每个线程都负责处理它自己的终止处理。

**terminate_function**类型在 EH 中定义。H 作为指向用户定义的终止函数的指针，*术语函数*返回**void**。 自定义函数*术语"函数*"不能采用任何参数，并且不应返回到其调用方。 如果是，则调用[中止](abort.md)。 不能从*术语函数*中引发异常。

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **set_terminate**函数仅在调试器外部工作。

对于所有动态链接的 DLL 或 EXEs，都有一个**set_terminate**处理程序;即使您调用**set_terminate**您的处理程序可能被另一个替换，或者您可能正在替换由另一个 DLL 或 EXE 设置的处理程序。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [terminate](terminate-crt.md) 的示例。

## <a name="see-also"></a>另请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[中止](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[终止](terminate-crt.md)<br/>
[意外](unexpected-crt.md)<br/>
