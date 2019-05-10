---
title: setjmp
ms.date: 08/14/2018
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 9f1a2b71a7b8fc7603c36938879348dca16288e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356415"
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

保存堆栈环境后，返回 0。 如果**setjmp**为返回`longjmp`调用，它将返回*值*参数`longjmp`，或者如果*值*自变量的`longjmp`为 0，**setjmp**返回 1。 无错误返回。

## <a name="remarks"></a>备注

**Setjmp**函数保存堆栈环境，你可以随后还原，使用`longjmp`。 结合使用时， **setjmp**并`longjmp`提供一种方法来执行非本地**goto**。 它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用常规调用或返回约定。

调用**setjmp**将在当前堆栈环境保存*env*。 随后调用`longjmp`还原保存的环境并将控件返回到点，紧跟在对应**setjmp**调用。 可供接收控件的例程访问的所有变量（寄存器变量除外）包含在调用 `longjmp` 时它们具有的值。

不能使用**setjmp**从托管代码到本机跳转。

**Microsoft 专用**

在 MicrosoftC++上 Windows，代码**longjmp**作为异常处理代码中使用相同的堆栈展开语义。 它是安全的使用在同一个位置C++可能引发异常。 但是，这种用法是不可移植，并附带的一些重要注意事项。 有关详细信息，请参阅[longjmp](longjmp.md)。

**结束 Microsoft 专用**

> [!NOTE]
> 在可移植C++代码，不能假定`setjmp`并`longjmp`支持C++对象的语义。 具体而言， `setjmp` / `longjmp`调用对行为未定义如果替换`setjmp`并`longjmp`通过**捕获**并**引发**像调用任何自动对象的任何非平常的析构函数。 在C++程序，我们建议你使用C++异常处理机制。

有关详细信息，请参阅[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_fpreset](fpreset.md) 的示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
