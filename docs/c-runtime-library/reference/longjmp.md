---
title: longjmp
ms.date: 08/14/2018
api_name:
- longjmp
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
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: b4527a29475f9e393dc5abf19b866d926bec2ccc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953133"
---
# <a name="longjmp"></a>longjmp

还原由`setjmp`调用设置的堆栈环境和执行区域设置。

## <a name="syntax"></a>语法

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>参数

*env*<br/>
存储变量的环境。

*value*<br/>
要返回到 `setjmp` 调用的值。

## <a name="remarks"></a>备注

**Longjmp**函数将还原以前通过`setjmp` *env*保存的堆栈环境和执行区域设置。 `setjmp`和**longjmp**提供了一种方法来执行非本地**goto**;它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用正常调用和返回约定。

对的调用`setjmp`会导致当前堆栈环境保存在*环境中。* 对**longjmp**的后续调用将还原保存的环境，并将控制权返回到紧靠相应`setjmp`调用之后的点。 执行将继续，就好像刚刚通过 `setjmp` 调用返回 *value* 一样。 例程接收控件可访问的所有变量（寄存器变量除外）的值包含在调用**longjmp**时所具有的值。 寄存器变量的值是不可预知的。 `setjmp` 返回的值必须为非零。 如果将 *value* 作为 0 传递，在实际返回中将替换值 1。

**Microsoft 专用**

在 Windows C++上的 Microsoft 代码中， **longjmp**使用与异常处理代码相同的堆栈展开语义。 可以安全地在可以引发C++异常的同一位置中使用。 但是，这种用法不可移植，并附带一些重要的注意事项。

仅在调用`setjmp`的函数返回前调用 longjmp，否则结果是不可预知的。

使用**longjmp**时，请注意以下限制：

- 不要假定寄存器变量的值保持不变。 执行`setjmp` **longjmp**后，无法将调用例程中的寄存器变量的值还原为正确的值。

- 除非中断是由浮点异常引起的，否则不要使用**longjmp**将控制转移出中断处理例程。 在这种情况下，如果第一次通过调用[_fpreset](fpreset.md)重新初始化浮点数学包，程序可能会通过**longjmp**从中断处理程序返回。

- 不要使用**longjmp**从 Windows 代码直接或间接调用的回调例程传输控件。

- 如果代码是使用 **/ehs**或 **/ehsc**编译的，并且包含**longjmp**调用的函数是**noexcept** ，则该函数中的本地对象在堆栈展开过程中可能不会被销毁。

**结束 Microsoft 专用**

> [!NOTE]
> 在可C++移植代码中，无法`setjmp`假定`longjmp`和C++支持对象语义。 具体而言， `setjmp`如果替换/ `setjmp` `longjmp`和被 catch 和 throw 替换为任何自动对象的任何非普通析构函数，则调用对具有未定义的行为。 `longjmp` 在C++程序中，我们建议使用C++异常处理机制。

有关详细信息，请参阅[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_fpreset](fpreset.md) 的示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
