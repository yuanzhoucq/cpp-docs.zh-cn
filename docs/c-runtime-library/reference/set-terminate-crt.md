---
title: set_terminate (CRT) | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_terminate
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e62dc1e4f99a1d2707c6e7b86c79e0ffc8aa027
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

安装你自己的终止例程调用**终止**。

## <a name="syntax"></a>语法

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>参数

*termFunction*<br/>
指向终止你编写的函数的指针。

## <a name="return-value"></a>返回值

将指针返回到上一个函数通过注册**set_terminate**以便稍后能还原上一个函数。 如果已设置上一个函数，返回的值可能用于还原默认行为;此值可能为**NULL**。

## <a name="remarks"></a>备注

**Set_terminate**函数安装*termFunction*由调用的函数作为**终止**。 **set_terminate**用于 c + + 异常处理和引发异常之前可能在程序中的任何点调用。 **终止**调用[中止](abort.md)默认情况下。 你可以更改此默认设置编写你自己的终止函数并调用**set_terminate**与作为其自变量函数的名称。 **终止**调用的最后一个函数的自变量被当作**set_terminate**。 执行任何所需清理任务后*termFunction*应退出程序。 如果它没有退出 （如果它返回其调用方），[中止](abort.md)调用。

在多线程环境中，终止单独为每个线程维护的函数。 每个新线程都需要安装自己的终止函数。 因此，每个线程都负责处理它自己的终止处理。

**Terminate_function**在 EH 中定义类型。作为用户定义终止函数的指针的 H *termFunction*返回**void**。 自定义函数*termFunction*可以采用任何参数，不应返回其调用方。 如果是这样，[中止](abort.md)调用。 在不引发异常*termFunction*。

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate**函数只能在调试器外部。

一个**set_terminate**处理程序所有动态链接的 Dll 或 Exe; 即使你调用**set_terminate**可能被另一个替换你的处理程序或你可能会替换设置由另一个处理程序DLL 或 EXE。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [terminate](terminate-crt.md) 的示例。

## <a name="see-also"></a>请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
