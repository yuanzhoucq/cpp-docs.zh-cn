---
title: setjmp
ms.date: 08/14/2018
api_name:
- setjmp
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: beaf56a03c1bd157257d604bfd0ebefb219d0225
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226146"
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

保存堆栈环境后，返回 0。 如果**setjmp**作为调用的结果返回 `longjmp` ，则返回的*值*参数 `longjmp` ; 如果的*值*参数 `longjmp` 为0，则**setjmp**返回1。 无错误返回。

## <a name="remarks"></a>备注

**Setjmp**函数保存堆栈环境，你可以随后使用来还原该环境 `longjmp` 。 一起使用时， **setjmp**并 `longjmp` 提供执行非本地的方法 **`goto`** 。 它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用常规调用或返回约定。

对**setjmp**的调用将当前堆栈环境*保存在环境*中。 对的后续调用将 `longjmp` 还原保存的环境，并在相应的**setjmp**调用之后立即将控制权返回到点。 可供接收控件的例程访问的所有变量（寄存器变量除外）包含在调用 `longjmp` 时它们具有的值。

不能使用**setjmp**从本机到托管代码进行跳转。

**Microsoft 专用**

在 Windows 上的 Microsoft c + + 代码中， **longjmp**使用与异常处理代码相同的堆栈展开语义。 可以安全地在可引发 c + + 异常的相同位置使用。 但是，这种用法不可移植，并附带一些重要的注意事项。 有关详细信息，请参阅[longjmp](longjmp.md)。

**结束 Microsoft 专用**

> [!NOTE]
> 在可移植的 c + + 代码中，不能假设 `setjmp` 并 `longjmp` 支持 c + + 对象语义。 具体而言， `setjmp` / `longjmp` 如果将和替换并 `setjmp` `longjmp` **`catch`** **`throw`** 将调用任何自动对象的任何非普通析构函数，则调用对的行为未定义。 在 c + + 程序中，建议使用 c + + 异常处理机制。

有关详细信息，请参阅[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_fpreset](fpreset.md) 的示例。

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
