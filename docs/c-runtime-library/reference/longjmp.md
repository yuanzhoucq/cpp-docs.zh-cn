---
title: longjmp | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a593c2dcdfe1731ee5c6438c7a330e7f4ea8740
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="longjmp"></a>longjmp

还原堆栈环境和执行区域设置。

## <a name="syntax"></a>语法

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>参数

*env*变量中存储的环境。

*值*值返回给**setjmp**调用。

## <a name="remarks"></a>备注

**Longjmp**函数还原之前保存在中的堆栈环境和执行区域设置*env*通过**setjmp**。 **setjmp**和**longjmp**提供一种执行本地**goto**; 它们通常用于将执行控制权传递给而无需以前调用的例程中的错误处理或恢复代码使用正常调用并返回约定。

调用**setjmp**使得当前堆栈环境保存在*env*。 后续调用**longjmp**还原保存的环境，并将控件返回到紧跟在对应的点**setjmp**调用。 执行将继续如同*值*仅具有已返回**setjmp**调用。 可供接收控件的例程访问的所有变量 （寄存器变量除外） 的值包含它们具有值**longjmp**调用。 寄存器变量的值是不可预知的。 返回的值**setjmp**必须为非零。 如果将 *value* 作为 0 传递，在实际返回中将替换值 1。

调用**longjmp**之前调用的函数**setjmp**返回; 否则结果是不可预知。

使用时，请注意以下限制**longjmp**:

- 不要假定寄存器变量的值保持不变。 例程的调用中的寄存器变量的值**setjmp**可能不会还原为正确值之后**longjmp**执行。

- 不要使用**longjmp**将控件转移出中断处理例程除非中断由浮点异常。 在这种情况下，程序可能会返回从中断处理程序通过**longjmp**如果它首先重新初始化浮点数学包通过调用 **_fpreset**。

     **请注意**时应小心谨慎**setjmp**和**longjmp** c + + 程序中。 由于这些函数不支持 C++ 对象语义，使用 C++ 异常处理机制更安全。

有关详细信息，请参阅[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

请参阅 [_fpreset](fpreset.md) 的示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)<br/>
