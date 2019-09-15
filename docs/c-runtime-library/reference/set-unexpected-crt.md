---
title: set_unexpected (CRT)
ms.date: 11/04/2016
api_name:
- set_unexpected
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
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: 77c8f0ae8c64423a656a2ebbe1fe3ef6dbe1b794
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948305"
---
# <a name="set_unexpected-crt"></a>set_unexpected (CRT)

安装要由 **unexpected** 调用的自身的终止函数。

## <a name="syntax"></a>语法

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>参数

*unexpFunction*<br/>
指向一个函数的指针，该函数用于替换**意外**的函数。

## <a name="return-value"></a>返回值

返回指向 **_set_unexpected**注册的上一个终止函数的指针，以便稍后可以还原以前的函数。 如果以前未设置函数，则返回值可用于还原默认行为;此值可以为**NULL**。

## <a name="remarks"></a>备注

**Set_unexpected**函数将*unexpFunction*安装为**意外**调用的函数。 当前C++异常处理实现中未**使用异常。** **Unexpected_function**类型在 EH 中定义。H 作为指向用户定义的意外函数的指针， *unexpFunction*返回**void**。 自定义*unexpFunction*函数不应返回到其调用方。

```cpp
typedef void ( *unexpected_function )( );
```

默认情况下，**意外**调用**终止**。 可以通过以下方式更改此默认行为：编写自己的终止函数并调用**set_unexpected** ，并将函数名称作为其参数。 **意外**调用作为**set_unexpected**的参数提供的最后一个函数。

与通过调用**set_terminate**安装的自定义终止函数不同， *unexpFunction*中可能会引发异常。

在多线程环境中，单独为每个线程维护意外函数。 每个新线程都需要安装它自己的意外函数。 因此，每个线程都负责它自己的意外处理。

在当前的C++异常处理实现中，**意外**调用会在默认情况下**终止**，并从不由异常处理运行时库调用。 不会有任何特定的优势来调用**意外**而不是**终止**。

所有动态链接的 Dll 或 Exe 都有一个**set_unexpected**的处理程序;即使您调用**set_unexpected** ，您的处理程序也可能被另一个 DLL 或 EXE 替换为其他 DLL 或 EXE。

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
