---
title: "setjmp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d13a24974a6c722301c6361a13f9d9178cd70220
ms.lasthandoff: 02/24/2017

---
# <a name="setjmp"></a>setjmp
保存程序的当前状态。  
  
## <a name="syntax"></a>语法  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### <a name="parameters"></a>参数  
 `env`  
 存储变量的环境。  
  
## <a name="return-value"></a>返回值  
 保存堆栈环境后，返回 0。 如果 `setjmp` 作为 `longjmp` 调用的结果返回，它将返回 `longjmp` 的参数 `value`，或者如果 `longjmp` 的参数 `value` 为 0，则 `setjmp` 返回 1。 无错误返回。  
  
## <a name="remarks"></a>备注  
 `setjmp` 函数保存堆栈环境，你随后可以使用 `longjmp` 对其进行还原。 结合使用时，`setjmp` 和 `longjmp` 提供可执行非本地 `goto` 的方法。 它们通常用于将执行控制传递给之前调用的例程中的错误处理或恢复代码，而不使用常规调用或返回约定。  
  
 对 `setjmp` 的调用会将当前堆栈环境保存在 `env` 中。 对 `longjmp` 的后续调用将还原保存的环境并将控件返回到紧跟在对应的 `setjmp` 调用后面的点。 可供接收控件的例程访问的所有变量（寄存器变量除外）包含在调用 `longjmp` 时它们具有的值。  
  
 不能使用 `setjmp` 从本机跳转到托管代码。  
  
 **注意** `setjmp` 和 `longjmp` 不支持 C++ 对象语义。 在 C++ 程序中，使用 C++ 异常处理机制。  
  
 有关详细信息，请参阅[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`setjmp`|\<setjmp.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_fpreset](../../c-runtime-library/reference/fpreset.md) 的示例。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [_setjmp3](../../c-runtime-library/setjmp3.md)
