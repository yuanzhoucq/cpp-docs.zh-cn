---
title: "longjmp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f80495e9c3e9fa7ce39dac8811e474f68844d196
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="longjmp"></a>longjmp
还原堆栈环境和执行区域设置。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void longjmp(  
   jmp_buf env,  
   int value   
);  
```  
  
#### <a name="parameters"></a>参数  
 `env`  
 存储变量的环境。  
  
 *value*  
 要返回到 `setjmp` 调用的值。  
  
## <a name="remarks"></a>备注  
 `longjmp` 函数还原之前由 `env` 保存在 `setjmp` 中的堆栈环境和执行区域设置。 `setjmp` 和 `longjmp` 提供了一个执行非本地 `goto` 的方法；它们通常有两个用途，一个用途是将执行控制权传递给之前调用的例程中的错误处理或恢复代码而不使用正常调用；另一个用途是返回约定。  
  
 对 `setjmp` 的调用将导致当前堆栈环境保存在 `env` 中。 对 `longjmp` 的后续调用将还原保存的环境并将控件返回到紧跟在对应的 `setjmp` 调用后面的点。 执行将继续，就好像刚刚通过 `setjmp` 调用返回 *value* 一样。 可供接收控件的例程访问的所有变量（寄存器变量除外）的值包含在调用 `longjmp` 时它们具有的值。 寄存器变量的值是不可预知的。 `setjmp` 返回的值必须为非零。 如果将 *value* 作为 0 传递，在实际返回中将替换值 1。  
  
 请在调用的 `longjmp` 的函数返回前调用 `setjmp`；否则结果是不可预知的。  
  
 在使用 `longjmp`时，请注意以下限制：  
  
-   不要假定寄存器变量的值保持不变。 执行 `setjmp` 后，调用 `longjmp` 的例程中的寄存器变量的值不能恢复为正确值。  
  
-   除非中断是由浮点异常引起的，否则不要使用 `longjmp` 将控件转移出中断处理例程。 在这种情况下，程序可能通过 `longjmp` 从中断处理程序返回，前提是它首先通过调用 `_fpreset` 重新初始化浮点数学包。  
  
     **注意** 在 C++ 程序中使用 `setjmp` 和 `longjmp` 时请小心谨慎。 由于这些函数不支持 C++ 对象语义，使用 C++ 异常处理机制更安全。  
  
 有关详细信息，请参阅[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`longjmp`|\<setjmp.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
 请参阅 [_fpreset](../../c-runtime-library/reference/fpreset.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [setjmp](../../c-runtime-library/reference/setjmp.md)