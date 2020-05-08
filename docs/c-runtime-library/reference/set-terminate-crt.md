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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 29b760d8831411142aad052fdef510efb0486747
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914520"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

安装**终止**时要调用的自己的终止例程。

## <a name="syntax"></a>语法

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>参数

*termFunction*<br/>
指向终止你编写的函数的指针。

## <a name="return-value"></a>返回值

返回指向**set_terminate**注册的上一个函数的指针，以便稍后可以还原以前的函数。 如果以前未设置函数，则返回值可用于还原默认行为;此值可以为**NULL**。

## <a name="remarks"></a>备注

**Set_terminate**函数将*termFunction*安装为**终止**时调用的函数。 **set_terminate**与 c + + 异常处理一起使用，并且在引发异常之前可在程序中的任意位置调用。 默认情况下，**终止**调用[中止](abort.md)。 可以通过以下方式更改此默认设置：编写自己的终止函数并调用**set_terminate** ，并将函数名称作为其参数。 **terminate**调用作为**set_terminate**的参数提供的最后一个函数。 执行任何所需的清除任务后， *termFunction*应退出程序。 如果不退出（如果它返回到其调用方），则调用[abort](abort.md) 。

在多线程环境中，终止单独为每个线程维护的函数。 每个新线程都需要安装自己的终止函数。 因此，每个线程都负责处理它自己的终止处理。

**Terminate_function**类型在 EH 中定义。H 作为指向用户定义的终止函数的指针， *termFunction*返回**void**。 自定义函数*termFunction*不能采用任何参数，并且不应返回到其调用方。 如果是，则调用[abort](abort.md) 。 不能从*termFunction*内部引发异常。

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate**函数仅在调试器外部运行。

所有动态链接的 Dll 或 Exe 都有单个**set_terminate**处理程序;即使你调用**set_terminate**你的处理程序也可能被另一个 DLL 或 EXE 替换。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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
[之外](unexpected-crt.md)<br/>
