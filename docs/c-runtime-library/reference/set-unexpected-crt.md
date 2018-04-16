---
title: "set_unexpected (CRT) | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: edc1d3b96ee5b52d349b30434932d2c9770267b4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)
安装要由 `unexpected` 调用的自身的终止函数。  
  
## <a name="syntax"></a>语法  
  
```  
unexpected_function set_unexpected(  
   unexpected_function unexpFunction   
);  
```  
  
#### <a name="parameters"></a>参数  
 `unexpFunction`  
 指向为替换 `unexpected` 函数而编写的函数的指针。  
  
## <a name="return-value"></a>返回值  
 返回指向由 `_set_unexpected` 注册的上一个终止函数的指针，以便稍后能还原上一个函数。 如果之前尚未设置函数，则返回值可用于还原默认行为；此值可能为 NULL。  
  
## <a name="remarks"></a>备注  
 `set_unexpected` 函数安装 `unexpFunction` 作为由 `unexpected` 调用的函数。 不会在当前 C++ 异常处理实现中使用 `unexpected`。 在 EH.H 中将 `unexpected_function` 类型定义为指向用户定义的意外函数的指针，则 `unexpFunction` 返回 `void`。 自定义的 `unexpFunction` 函数不应返回到其调用方。  
  
```  
typedef void ( *unexpected_function )( );  
```  
  
 默认情况下，`unexpected` 调用 `terminate`。 你可以通过以下方式更改此默认行为：编写自己的终止函数并调用 `set_unexpected`（将该函数的名称作为其参数）。 `unexpected` 调用作为 `set_unexpected` 的参数提供的最后一个函数。  
  
 与通过对 `set_terminate` 的调用所安装的自定义终止函数不同，可能会从 `unexpFunction` 中引发异常。  
  
 在多线程环境中，单独为每个线程维护意外函数。 每个新线程都需要安装它自己的意外函数。 因此，每个线程都负责它自己的意外处理。  
  
 在当前 C++ 异常处理的 Microsoft 实现中，`unexpected` 默认调用 `terminate`，且始终不由异常处理运行时库进行调用。 调用 `unexpected` 而不是 `terminate` 并没有特别的优势。  
  
 存在适用于所有动态链接的 DLL 或 EXE 的单个 `set_unexpected` 处理程序；即使你调用 `set_unexpected`，你的处理程序也可能会替换为另一个处理程序，或者你也要使用另一个 DLL 或 EXE 替换处理程序集。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`set_unexpected`|\<eh.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [异常处理例程](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_get_unexpected](../../c-runtime-library/reference/get-unexpected.md)   
 [set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)