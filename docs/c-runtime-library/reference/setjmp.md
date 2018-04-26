---
title: setjmp | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- setjmp
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
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc01f80aa4521ff3588cca14ceabbf5447338cca
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="setjmp"></a>setjmp

保存程序的当前状态。

## <a name="syntax"></a>语法

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>参数

*env*<br/>
存储变量的环境。

## <a name="return-value"></a>返回值

保存堆栈环境后，返回 0。 如果**setjmp**返回的结果**longjmp**调用，它将返回**值**参数**longjmp**，或者如果**值**参数**longjmp**为 0， **setjmp**返回 1。 无错误返回。

## <a name="remarks"></a>备注

**Setjmp**函数将保存的堆栈环境，你可以随后将还原，使用**longjmp**。 一起使用时， **setjmp**和**longjmp**提供一种执行非本地**goto**。 它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用常规调用或返回约定。

调用**setjmp**将保存当前的堆栈环境的*env*。 后续调用**longjmp**还原保存的环境和相应后立即将控制权返回给点**setjmp**调用。 （除外寄存器变量） 可供接收控件的例程访问的所有变量都包含的值，它们具有**longjmp**调用。

不能使用**setjmp**从托管代码的本机跳转。

**请注意** **setjmp**和**longjmp**不支持 c + + 对象语义。 在 C++ 程序中，使用 C++ 异常处理机制。

有关详细信息，请参阅[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_fpreset](fpreset.md) 的示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)<br/>
[_setjmp3](../../c-runtime-library/setjmp3.md)<br/>
