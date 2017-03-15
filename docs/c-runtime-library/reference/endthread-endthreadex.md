---
title: "_endthread、_endthreadex | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _endthread
- _endthreadex
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
- _endthread
- endthreadex
- _endthreadex
- endthread
dev_langs:
- C++
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: e1e2211a34a7cc146d1ce3b791927ffc206edaef
ms.lasthandoff: 02/24/2017

---
# <a name="endthread-endthreadex"></a>_endthread、_endthreadex
终止线程； `_endthread` 终止由 `_beginthread` 创建的线程，  `_endthreadex` 终止由`_beginthreadex`创建的线程。  
  
## <a name="syntax"></a>语法  
  
```  
void _endthread( void );  
void _endthreadex(   
   unsigned retval   
);  
```  
  
#### <a name="parameters"></a>参数  
 `retval`  
 线程退出代码。  
  
## <a name="remarks"></a>备注  
 可以显式调用 `_endthread` 或 `_endthreadex` 终止线程；但是，当线程从作为 `_endthread` 或 `_endthreadex` 参数传递的例程中返回时，会自动调用 `_beginthread` 或 `_beginthreadex`。 通过对 `endthread` 或 `_endthreadex` 的调用来终止线程有助于确保适当恢复为线程分配的资源。  
  
> [!NOTE]
>  对于与 Libcmt.lib 链接的可执行文件，请不要调用 Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) API；这将阻止运行时系统回收已分配的资源。 `_endthread` 和 `_endthreadex` 回收分配的线程资源，然后调用 `ExitThread`。  
  
 `_endthread` 会自动关闭线程句柄。 （该行为与 Win32 `ExitThread` API 不同。）因此，使用 `_beginthread` 和 `_endthread` 时，请不要通过调用 Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) API 来显式关闭线程句柄。  
  
 与 Win32 `ExitThread` API 相同， `_endthreadex` 不会关闭线程句柄。 因此，当你使用 `_beginthreadex` 和 `_endthreadex` 时，必须通过调用 Win32 `CloseHandle` API 来关闭线程句柄。  
  
> [!NOTE]
>  `_endthread` 和 `_endthreadex` 会导致 C++ 析构函数在不会调用的线程中处于挂起状态。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_endthread`|\<process.h>|  
|`_endthreadex`|\<process.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md) 的多线程版本。  
  
## <a name="example"></a>示例  
 请参阅 [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) 示例。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_beginthread、_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)
