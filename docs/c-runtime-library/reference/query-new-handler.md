---
title: "_query_new_handler | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _query_new_handler
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _query_new_handler
- query_new_handler
dev_langs:
- C++
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: d79c8a5d68f7dd41a737111a3abe943389bfedd2
ms.lasthandoff: 02/24/2017

---
# <a name="querynewhandler"></a>_query_new_handler
返回当前新处理程序例程的地址。  
  
## <a name="syntax"></a>语法  
  
```  
_PNH _query_new_handler(  
   void   
);  
```  
  
## <a name="return-value"></a>返回值  
 返回由 `_set_new_handler` 设置的当前新处理程序例程的地址。  
  
## <a name="remarks"></a>备注  
 C++ `_query_new_handler` 函数返回由 C++ [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 函数设置的当前异常处理函数的地址。 如果 **new** 运算符无法分配内存，则 `_set_new_handler` 用于指定获取控制权的异常处理函数。 有关详细信息，请参阅“C++ 语言参考”中的 [new 和 delete 运算符](../../cpp/new-and-delete-operators.md)的讨论。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_query_new_handler`|\<new.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)
