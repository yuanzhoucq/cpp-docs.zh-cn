---
title: "_set_new_mode | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_new_mode
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
- set_new_mode
- _set_new_mode
dev_langs:
- C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: 14
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 57a578f8accf7244d71c0d8791a6e898ead7d242
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="setnewmode"></a>_set_new_mode
设置 `malloc` 的新处理程序模式。  
  
## <a name="syntax"></a>语法  
  
```  
int _set_new_mode(  
   int newhandlermode   
);  
```  
  
#### <a name="parameters"></a>参数  
 `newhandlermode`  
 `malloc` 的新处理程序模式；有效值为 0 或 1。  
  
## <a name="return-value"></a>返回值  
 返回为 `malloc` 设置的上一个处理程序模式。 返回值 1 表示，分配内存失败后，`malloc` 之前已调用新的处理程序例程；返回值 0 表示未执行此操作。 如果`newhandlermode`参数不等于 0 或 1 时，将返回-1。  
  
## <a name="remarks"></a>备注  
 C++ `_set_new_mode` 函数将为 [malloc](../../c-runtime-library/reference/malloc.md) 设置新的处理程序模式。 新的处理程序模式将指示 `malloc` 是否在失败时调用由 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 设置的新处理程序例程。 默认情况下，`malloc` 在失败时不调用新的处理程序例程来分配内存。 可以替代此默认行为，以便在 `malloc` 无法分配内存时，`malloc` 将以 `new` 运算符由于相同原因失败时的同一方法调用新的处理程序例程。 有关详细信息，请参阅 *C++ 语言参考*中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 运算符。 若要重写默认值，请调用：  
  
```  
_set_new_mode(1)  
```  
  
 在程序的早期进行调用，或链接到 Newmode.obj（请参阅[链接选项](../../c-runtime-library/link-options.md)）。  
  
 此函数验证其参数。 如果 `newhandlermode` 不为 0 或 1，此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则 **_**`set_new_mode` 返回 -1，并将 `errno` 设置为 `EINVAL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_set_new_mode`|\<new.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler](../../c-runtime-library/reference/query-new-handler.md)   
 [_query_new_mode](../../c-runtime-library/reference/query-new-mode.md)
