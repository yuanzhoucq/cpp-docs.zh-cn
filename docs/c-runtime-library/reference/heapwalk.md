---
title: "_heapwalk | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapwalk"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "heapwalk"
  - "_heapwalk"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_heapwalk 函数"
  - "调试 [CRT], 与堆有关的问题"
  - "heapwalk 函数"
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _heapwalk
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

遍历堆并返回有关下项的信息。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。除非调试时。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _heapwalk(   
   _HEAPINFO *entryinfo   
);  
```  
  
#### 参数  
 `entryinfo`  
 包含堆信息的缓冲区。  
  
## 返回值  
 `_heapwalk` 返回在 Malloc.h 定义的以下整数清单常数之一。  
  
 `_HEAPBADBEGIN`  
 无效或未找到的初始头信息。  
  
 `_HEAPBADNODE`  
 堆损坏或找到错误节点。  
  
 `_HEAPBADPTR`  
 `_HEAPINFO` 结构的`_pentry` 字段不包含有效的堆指针或 `entryinfo` 是一个空指针。  
  
 `_HEAPEND`  
 已成功到达的堆的末尾。  
  
 `_HEAPEMPTY`  
 堆尚未初始化  
  
 `_HEAPOK`  
 目前没有错误；`entryinfo` 更新相关下项堆的信息。  
  
 此外，如果发生错误，`_heapwalk` 设置 `errno` 到 `ENOSYS`。  
  
## 备注  
 `_heapwalk` 功能帮助调试堆相关的问题。  函数通过遍历堆，遍历项的每个调用，并返回指向包含有关下堆项的信息类型 `_HEAPINFO` 的结构。  `_HEAPINFO` 类型，定义在 Malloc.h，包含以下元素。  
  
 `int *_pentry`  
 堆项指针。  
  
 `size_t _size`  
 堆项的大小。  
  
 `int _useflag`  
 指示堆项是否正在使用的标志。  
  
 返回 `_HEAPOK` 存储项的大小 `_size` 字段并设置 `_useflag` 字段设置为 `_FREEENTRY` 或 `_USEDENTRY` \(可 `_heapwalk` 的调用两者都在 Malloc.h 定义的常数\)。  在堆中获取第一项的信息，通过 `_heapwalk` 指向 `_pentry` 成员是 `NULL`的 `_HEAPINFO` 结构。  如果操作系统不支持 `_heapwalk`\(例如，Windows 98\)，则该函数返回 `_HEAPEND` 并设置`errno` 为 `ENOSYS`。  
  
 此函数验证其参数。  如果 `entryinfo` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`_HEAPBADPTR`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_heapwalk`|\<malloc.h\>|\<errno.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
  
  **使用的块在0100的00310650**  
 **使用的块在0800的00310758**  
 **使用的块在0800的00310F60**  
 **使用的块在0398的00310FF0**  
 **使用的块在000D的00311390**  
 **使用的块在00B4的003113A8**  
 **使用的块在0034的00311468**  
 **使用的块在0039的003114A8**  
**...**  
 **使用的块在0010的00312228**  
 **使用的块在1000的00312240**  
 **使用的块在1DB0的00313250**  
**好\-堆的结尾**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)   
 [\_heapadd](../../c-runtime-library/heapadd.md)   
 [\_heapchk](../../c-runtime-library/reference/heapchk.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [\_heapset](../../c-runtime-library/heapset.md)