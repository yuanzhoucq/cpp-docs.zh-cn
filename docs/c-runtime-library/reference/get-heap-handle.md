---
title: "_get_heap_handle | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_heap_handle
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
- _get_heap_handle
- get_heap_handle
dev_langs:
- C++
helpviewer_keywords:
- heap functions
- memory allocation, heap memory
- _get_heap_handle function
- get_heap_handle function
ms.assetid: a4d05049-8528-494a-8281-a470d1e1115c
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2e8c08ed0ccffb7196133de89d4b9588333e1bfa
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="getheaphandle"></a>_get_heap_handle
返回 C 运行时系统所用堆的句柄。  
  
## <a name="syntax"></a>语法  
  
```  
intptr_t _get_heap_handle( void );  
```  
  
## <a name="return-value"></a>返回值  
 返回 C 运行时系统所用 Win32 堆的句柄。  
  
## <a name="remarks"></a>备注  
 如果想要针对 CRT 堆调用 [HeapSetInformation](http://msdn.microsoft.com/library/windows/desktop/aa366705) 并启用低分片堆，请使用此函数。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_get_heap_handle`|\<malloc.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="sample"></a>示例  
  
```  
// crt_get_heap_handle.cpp  
// compile with: /MT  
#include <windows.h>  
#include <malloc.h>  
#include <stdio.h>  
  
int main(void)  
{  
    intptr_t hCrtHeap = _get_heap_handle();  
    ULONG ulEnableLFH = 2;  
    if (HeapSetInformation((PVOID)hCrtHeap,  
                           HeapCompatibilityInformation,  
                           &ulEnableLFH, sizeof(ulEnableLFH)))  
        puts("Enabling Low Fragmentation Heap succeeded");  
    else  
        puts("Enabling Low Fragmentation Heap failed");  
    return 0;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)
