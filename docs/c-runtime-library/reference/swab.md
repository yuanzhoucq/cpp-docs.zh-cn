---
title: "_swab | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
dev_langs:
- C++
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01f23047436b7ff8cee16b42cc6ae0d8c2a9fd78
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="swab"></a>_swab
交换字节。  
  
## <a name="syntax"></a>语法  
  
```  
void _swab(  
   char *src,  
   char *dest,  
   int n   
);  
```  
  
## <a name="parameters"></a>参数  
 `src`  
 要复制和交换的数据。  
  
 `dest`  
 已交换数据的存储位置。  
  
 `n`  
 要复制和交换的字节数。  
  
## <a name="return-value"></a>返回值
 `swab` 函数不返回值。 如果 `src` 或 `dest` 指针为空指针或 `n` 小于零，则函数将 `errno` 设置为 `EINVAL`，并调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
 有关此代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。
 
## <a name="remarks"></a>备注  
 如果 `n` 值为偶数，`_swab` 函数将从 `n` 复制 `src` 个字节，交换每对相邻的字节，并将结果存储在 `dest` 上。 如果 `n` 为奇数，则 `_swab` 复制并交换 `src` 的前 `n-1` 字节，而并不复制最后一个字节。 `_swab` 函数通常用于准备要传输到使用不同的字节顺序的计算机的二进制数据。  
  
## <a name="requirements"></a>惠?  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_swab`|C：\<stdlib.h> C++：\<cstdlib> 或 \<stdlib.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
```C 
// crt_swab.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";  
char to[] =   "...........................";  
  
int main()  
{  
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);  
    _swab(from, to, sizeof(from));  
    printf("After:  %s\n        %s\n\n", from, to);  
}  
```  
  
```Output  
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes  
        ...........................  
  
After:  BADCFEHGJILKNMPORQTSVUXWZY  
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.  
```  
  
## <a name="see-also"></a>请参阅  
 [缓冲区操作](../../c-runtime-library/buffer-manipulation.md)