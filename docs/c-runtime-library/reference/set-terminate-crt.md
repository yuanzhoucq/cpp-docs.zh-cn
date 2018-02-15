---
title: "set_terminate (CRT) | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_terminate
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eba062bd1b791f055b2ae1c74c2a0107a4039d23
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="setterminate-crt"></a>set_terminate (CRT)
安装 `terminate` 将调用的自身的终止例程。  
  
## <a name="syntax"></a>语法  
  
```  
terminate_function set_terminate(  
   terminate_function termFunction  
);  
```  
  
#### <a name="parameters"></a>参数  
 `termFunction`  
 指向终止你编写的函数的指针。  
  
## <a name="return-value"></a>返回值  
 返回指向由 `set_terminate` 注册的上一个函数的指针，以便稍后能还原上一个函数。 如果之前尚未设置函数，则返回值可用于还原默认行为；此值可能为 NULL。  
  
## <a name="remarks"></a>备注  
 `set_terminate` 函数安装 `termFunction` 作为由 `terminate` 调用的函数。 `set_terminate` 与 C++ 异常处理一起使用，在引发异常之前可以在程序中的任意位置对其进行调用。 默认情况下，`terminate` 调用 `abort`。 可以通过以下方式更改此默认行为：编写自己的终止函数并调用 `set_terminate`（将该函数的名称作为其参数）。 `terminate` 调用作为 `set_terminate` 的参数提供的最后一个函数。 执行任何所需的清除任务后，`termFunction` 应退出程序。 如果没有退出（如果返回到其调用方），则调用 `abort`。  
  
 在多线程环境中，终止单独为每个线程维护的函数。 每个新线程都需要安装自己的终止函数。 因此，每个线程都负责处理它自己的终止处理。  
  
 在 EH.H 中将 `terminate_function` 类型定义为指向用户定义的终止函数的指针，则 `termFunction` 返回 `void`。 自定义函数 `termFunction` 可以不采用参数，也不应返回到其调用方。 否则调用 `abort`。 不从 `termFunction` 中引发异常。  
  
```  
typedef void ( *terminate_function )( );  
```  
  
> [!NOTE]
>  `set_terminate` 函数仅在调试器外部工作。  
  
 存在适用于所有动态链接的 DLL 或 EXE 的单个 `set_terminate` 处理程序；即使你调用 `set_terminate`，你的处理程序也可能会替换为另一个处理程序，或者你也要使用另一个 DLL 或 EXE 替换处理程序集。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`set_terminate`|\<eh.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 请参阅 [terminate](../../c-runtime-library/reference/terminate-crt.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [异常处理例程](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_get_terminate](../../c-runtime-library/reference/get-terminate.md)   
 [set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)