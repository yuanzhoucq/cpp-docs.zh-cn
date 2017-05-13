---
title: "_query_new_mode | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 414bbd73f44a51ab1ec35c9fb2bd8b3914c1ea8d
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="querynewmode"></a>_query_new_mode
返回指示由 `_set_new_mode` 为 `malloc` 设置的新处理程序模式的整数。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## <a name="return-value"></a>返回值  
 为 `malloc` 返回当前新处理程序模式，即 0 或 1。 返回值 1 表示在分配内存失败时，`malloc` 调用新的处理程序例程；返回值 0 表示不执行此操作。  
  
## <a name="remarks"></a>备注  
 C++ `_query_new_mode` 函数返回一个整数，指示由 [malloc](../../c-runtime-library/reference/malloc.md) 的 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函数设置的新处理程序模式。 新处理程序模式将指示 `malloc` 是否在分配内存失败时调用由 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的新处理程序例程。 默认情况下，`malloc` 不会在失败时调用新的处理程序例程。 可以使用 `_set_new_mode` 来重写此行为，以便在失败时，`malloc` 调用新的处理程序例程，方法与 **new** 运算符无法分配内存时所执行的操作一样。 有关详细信息，请参阅“C++ 语言参考”中的 [new 和 delete 运算符](../../cpp/new-and-delete-operators.md)的讨论。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_query_new_mode`|\<new.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler](../../c-runtime-library/reference/query-new-handler.md)
