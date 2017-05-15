---
title: "_heapwalk | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _heapwalk
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
- heapwalk
- _heapwalk
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
caps.latest.revision: 22
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
ms.openlocfilehash: 936ca2f3f4e4f2fb57dd730f5a58927d08d6207f
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="heapwalk"></a>_heapwalk
遍历堆，并返回与下一个条目有关的信息。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序，调试版本除外。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _heapwalk(   
   _HEAPINFO *entryinfo   
);  
```  
  
#### <a name="parameters"></a>参数  
 `entryinfo`  
 要包含堆信息的缓冲区。  
  
## <a name="return-value"></a>返回值  
 `_heapwalk` 返回 Malloc.h 中定义的以下整数清单常量之一。  
  
 `_HEAPBADBEGIN`  
 初始标头信息无效或未找到。  
  
 `_HEAPBADNODE`  
 堆已损坏或找到错误节点。  
  
 `_HEAPBADPTR`  
结构为 `_HEAPINFO` 的  `_pentry` 字段不会将有效指针包含在堆中，否则 `entryinfo` 将为 null 指针。  
  
 `_HEAPEND`  
 已成功到达堆结尾。  
  
 `_HEAPEMPTY`  
 堆未初始化。  
  
 `_HEAPOK`  
 到目前为止没有错误；有关下一个堆条目的信息已更新到 `entryinfo`。  
  
 此外，如果出现错误，`_heapwalk` 会将 `errno` 设置为 `ENOSYS`。  
  
## <a name="remarks"></a>备注  
 `_heapwalk` 函数帮助处理程序中与调试堆有关的问题。 该函数遍历堆，每次调用都遍历一个条目，并返回一个指向类型为 `_HEAPINFO` 的结构的指针，其中包含有关下一个堆条目的信息。 Malloc.h 中定义的 `_HEAPINFO` 类型包含以下元素。  
  
 `int *_pentry`  
 堆条目指针。  
  
 `size_t _size`  
 堆条目大小。  
  
 `int _useflag`  
 该标志指明堆条目是否正在使用中。  
  
 调用将返回 `_HEAPOK` 的 `_heapwalk` 时，会将条目大小存储在 `_size` 字段中并设置 `_useflag` 字段为 `_FREEENTRY` 或 `_USEDENTRY`（两者都是在 Malloc.h 中定义的常量）。 若要获取有关堆中第一个条目的信息，将指向 `_HEAPINFO` 结构的指针传递给 `_heapwalk`，结构的 `_pentry` 成员为 `NULL`。 如果操作系统不支持 `_heapwalk`（例如 Windows 98），则此函数将返回 `_HEAPEND`，并将 `errno` 设置为 `ENOSYS`。  
  
 此函数验证其参数。 如果 `entryinfo` 是一个 null 指针，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `_HEAPBADPTR`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_heapwalk`|\<malloc.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_heapwalk.c  
  
// This program "walks" the heap, starting  
// at the beginning (_pentry = NULL). It prints out each  
// heap entry's use, location, and size. It also prints  
// out information about the overall state of the heap as  
// soon as _heapwalk returns a value other than _HEAPOK  
// or if the loop has iterated 100 times.  
  
#include <stdio.h>  
#include <malloc.h>  
  
void heapdump(void);  
  
int main(void)  
{  
    char *buffer;  
  
    heapdump();  
    if((buffer = (char *)malloc(59)) != NULL)  
    {  
        heapdump();  
        free(buffer);  
    }  
    heapdump();  
}  
  
void heapdump(void)  
{  
    _HEAPINFO hinfo;  
    int heapstatus;  
    int numLoops;  
    hinfo._pentry = NULL;  
    numLoops = 0;  
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&  
          numLoops < 100)  
    {  
        printf("%6s block at %Fp of size %4.4X\n",  
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),  
               hinfo._pentry, hinfo._size);  
        numLoops++;  
    }  
  
    switch(heapstatus)  
    {  
    case _HEAPEMPTY:  
        printf("OK - empty heap\n");  
        break;  
    case _HEAPEND:  
        printf("OK - end of heap\n");  
        break;  
    case _HEAPBADPTR:  
        printf("ERROR - bad pointer to heap\n");  
        break;  
    case _HEAPBADBEGIN:  
        printf("ERROR - bad start of heap\n");  
        break;  
    case _HEAPBADNODE:  
        printf("ERROR - bad node in heap\n");  
        break;  
    }  
}  
```  
  
```Output  
  USED block at 00310650 of size 0100  
  USED block at 00310758 of size 0800  
  USED block at 00310F60 of size 0080  
  FREE block at 00310FF0 of size 0398  
  USED block at 00311390 of size 000D  
  USED block at 003113A8 of size 00B4  
  USED block at 00311468 of size 0034  
  USED block at 003114A8 of size 0039  
...  
  USED block at 00312228 of size 0010  
  USED block at 00312240 of size 1000  
  FREE block at 00313250 of size 1DB0  
OK - end of heap  
```  
  
## <a name="see-also"></a>另请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [_heapadd](../../c-runtime-library/heapadd.md)   
 [_heapchk](../../c-runtime-library/reference/heapchk.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [_heapset](../../c-runtime-library/heapset.md)
