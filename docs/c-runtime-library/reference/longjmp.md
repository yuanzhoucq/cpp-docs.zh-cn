---
title: longjmp
ms.date: 08/14/2018
apiname:
- longjmp
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
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: 56f050b5f59767fff04586d7d985cafe6d529b83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626702"
---
# <a name="longjmp"></a>longjmp

还原堆栈环境和执行区域设置设置`setjmp`调用。

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

**Longjmp**函数还原之前保存在中的堆栈环境和执行区域设置*env*通过`setjmp`。 `setjmp` 并**longjmp**提供一种方法来执行非本地**goto**; 它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而无需使用普通的调用并返回约定。

调用`setjmp`会导致当前堆栈环境保存在*env*。 随后调用**longjmp**还原保存的环境，并将控制权返回给紧跟在对应的点`setjmp`调用。 执行将继续，就好像刚刚通过 `setjmp` 调用返回 *value* 一样。 接收控件的例程可访问的所有变量 （寄存器变量除外） 的值包含它们具有的值**longjmp**调用。 寄存器变量的值是不可预知的。 `setjmp` 返回的值必须为非零。 如果将 *value* 作为 0 传递，在实际返回中将替换值 1。

**Microsoft 专用**

在 Windows 中，Microsoft c + + 代码中**longjmp**为异常处理代码中使用相同的堆栈展开语义。 它可以安全地使用可引发 c + + 异常的相同位置。 但是，这种用法是不可移植，并附带的一些重要注意事项。

只能调用**longjmp**在调用该函数前`setjmp`返回; 否则结果不可预知。

使用时请注意以下限制**longjmp**:

- 不要假定寄存器变量的值保持不变。 例程的调用中的寄存器变量的值`setjmp`可能不会还原为正确值之后**longjmp**执行。

- 不要使用**longjmp**将控件转移出中断处理例程除非中断由浮点异常。 在这种情况下，程序可能会返回从中断处理程序通过**longjmp**如果它首先会重新初始化浮点数学包通过调用[_fpreset](fpreset.md)。

- 不要使用**longjmp**将控制权从由 Windows 代码直接或间接调用的回调例程。

- 如果使用会将代码编译 **/EHs**或 **/EHsc**和包含该函数**longjmp**调用**noexcept**然后本地对象中的函数不可能在堆栈展开过程销毁。

**结束 Microsoft 专用**

> [!NOTE]
> 在可移植 c + + 代码中，不能假定`setjmp`和`longjmp`支持 c + + 对象语义。 具体而言， `setjmp` / `longjmp`调用对行为未定义如果替换`setjmp`并`longjmp`通过**捕获**并**引发**像调用任何自动对象的任何非平常的析构函数。 在 c + + 程序中，我们建议使用 c + + 异常处理机制。

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
