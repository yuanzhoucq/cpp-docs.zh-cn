---
title: set_unexpected (CRT) | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7af5cce0b17747beb8c136f75489025d741f864a
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

安装要由 **unexpected** 调用的自身的终止函数。

## <a name="syntax"></a>语法

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>参数

*unexpFunction*<br/>
为替换而编写的函数指针**意外**函数。

## <a name="return-value"></a>返回值

返回指向以前的终止函数的注册的 **_set_unexpected**以便稍后能还原上一个函数。 如果已设置上一个函数，返回的值可能用于还原默认行为;此值可能为**NULL**。

## <a name="remarks"></a>备注

**Set_unexpected**函数安装*unexpFunction*由调用的函数作为**意外**。 **意外**不在当前的 c + + 异常处理实现中使用。 **Unexpected_function**在 EH 中定义类型。作为用户定义的意外函数，指针 H *unexpFunction*返回**void**。 您的自定义*unexpFunction*函数不应返回其调用方。

```cpp
typedef void ( *unexpected_function )( );
```

默认情况下，**意外**调用**终止**。 你可以更改此默认行为： 编写你自己的终止函数并调用**set_unexpected**与作为其自变量函数的名称。 **意外**调用的最后一个函数的自变量被当作**set_unexpected**。

与安装通过调用自定义终止函数不同**set_terminate**，可能会引发异常，从*unexpFunction*。

在多线程环境中，单独为每个线程维护意外函数。 每个新线程都需要安装它自己的意外函数。 因此，每个线程都负责它自己的意外处理。

在当前的 Microsoft 实现的 c + + 异常处理，**意外**调用**终止**默认情况下，永远不会调用异常处理运行时库。 没有特定于调用优势**意外**而非**终止**。

一个**set_unexpected**处理程序所有动态链接的 Dll 或 Exe; 即使你调用**set_unexpected**可能由另一个替换你的处理程序或你正在替换处理程序集另一个 DLL 或 EXE。

## <a name="requirements"></a>要求

|例程|必需的标头|
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
