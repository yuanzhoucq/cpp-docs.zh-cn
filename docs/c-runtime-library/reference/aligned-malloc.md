---
title: "_aligned_malloc | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_malloc"
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
  - "_aligned_malloc"
  - "alligned_malloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_aligned_malloc 函数"
  - "aligned_malloc 函数"
ms.assetid: fb788d40-ee94-4039-aa4d-97d73dab1ca0
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_malloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定对齐边界分配内存。  
  
## 语法  
  
```  
void * _aligned_malloc(  
    size_t size,   
    size_t alignment  
);  
```  
  
#### 参数  
 `size`  
 请求的内存分配的大小。  
  
 `alignment`  
 对齐值，必须是 2 的整数次幂。  
  
## 返回值  
 指向已分配的内存块的指针或 `NULL`（如果操作失败）。  指针是一个多重 `alignment`。  
  
## 备注  
 `_aligned_malloc` 基于 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 `_aligned_malloc` 被标记为 `__declspec(noalias)` 和 `__declspec(restrict)`，也就是说确保该函数不能修改全局变量，并且指针返回不使用别名。  有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。  
  
 如果内存分配失败或请求的大小大于 `errno`，则此函数会将 `ENOMEM` 设置为 `_HEAP_MAXREQ`。  有关 `errno` 的详细信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外，`_aligned_malloc` 将验证其参数。  如果 `alignment` 不是 2 的幂或 `size` 是零，则此函数调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则此函数将返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_aligned_malloc`|\<malloc.h\>|  
  
## 示例  
  
```  
// crt_aligned_malloc.c  
  
#include <malloc.h>  
#include <stdio.h>  
  
int main() {  
    void    *ptr;  
    size_t  alignment,  
            off_set;  
  
    // Note alignment should be 2^N where N is any positive int.  
    alignment = 16;  
    off_set = 5;  
  
    // Using _aligned_malloc  
    ptr = _aligned_malloc(100, alignment);  
    if (ptr == NULL)  
    {  
        printf_s( "Error allocation aligned memory.");  
        return -1;  
    }  
    if (((unsigned long long)ptr % alignment ) == 0)  
        printf_s( "This pointer, %p, is aligned on %zu\n",  
                  ptr, alignment);  
    else  
        printf_s( "This pointer, %p, is not aligned on %zu\n",   
                  ptr, alignment);  
  
    // Using _aligned_realloc  
    ptr = _aligned_realloc(ptr, 200, alignment);  
    if ( ((unsigned long long)ptr % alignment ) == 0)  
        printf_s( "This pointer, %p, is aligned on %zu\n",  
                  ptr, alignment);  
    else  
        printf_s( "This pointer, %p, is not aligned on %zu\n",   
                  ptr, alignment);  
    _aligned_free(ptr);  
  
    // Using _aligned_offset_malloc  
    ptr = _aligned_offset_malloc(200, alignment, off_set);  
    if (ptr == NULL)  
    {  
        printf_s( "Error allocation aligned offset memory.");  
        return -1;  
    }  
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)  
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",  
                  ptr, off_set, alignment);  
    else  
        printf_s( "This pointer, %p, does not satisfy offset %zu "  
                  "and alignment %zu\n",ptr, off_set, alignment);  
  
    // Using _aligned_offset_realloc  
    ptr = _aligned_offset_realloc(ptr, 200, alignment, off_set);  
    if (ptr == NULL)  
    {  
        printf_s( "Error reallocation aligned offset memory.");  
        return -1;  
    }  
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)  
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",  
                  ptr, off_set, alignment);  
    else  
        printf_s( "This pointer, %p, does not satisfy offset %zu and "  
                  "alignment %zu\n", ptr, off_set, alignment);  
  
    // Note that _aligned_free works for both _aligned_malloc  
    // and _aligned_offset_malloc. Using free is illegal.  
    _aligned_free(ptr);  
}  
```  
  
  **指针 3280880，在 16 上对齐**  
**指针 3280880，在 16 上对齐**  
**指针 3280891，在与 16 对齐的基础上偏移 5**  
**指针 3280891，在与 16 对齐的基础上偏移 5**   
## 请参阅  
 [数据对齐](../../c-runtime-library/data-alignment.md)