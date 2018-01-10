---
title: "remove、_wremove |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wremove
- remove
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- remove
- _wremove
- _tremove
dev_langs: C++
helpviewer_keywords:
- tremove function
- _wremove function
- files [C++], deleting
- _tremove function
- files [C++], removing
- wremove function
- remove function
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11050e3f168f390fa7a80aa6febf08a4be695c3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="remove-wremove"></a>remove、_wremove
删除文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int remove(  
   const char *path   
);  
int _wremove(  
   const wchar_t *path   
);  
```  
  
#### <a name="parameters"></a>参数  
 *path*  
 要移除的文件的路径。  
  
## <a name="return-value"></a>返回值  
 如果成功删除文件，则这些函数将返回 0。 否则，它将返回 -1 并将 `errno` 设置为 `EACCES`，以指示路径指定只读文件或文件已打开，或设置为 **ENOENT**，以指示未找到文件名或路径，或者路径指定目录。  
  
 有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 **remove** 函数删除由  *路径指定的文件。* `_wremove` 是 **_remove** 的宽字符版本；`_wremove` 的 *path* 参数是宽字符字符串。 `_wremove` 和 **_remove** 的行为完全相同。 必须先结束对文件的所有处理，然后才能删除文件。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tremove`|**remove**|**remove**|`_wremove`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|**remove**|\<stdio.h> 或 \<io.h>|  
|`_wremove`|\<stdio.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_remove.c  
/* This program uses remove to delete crt_remove.txt */  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( remove( "crt_remove.txt" ) == -1 )  
      perror( "Could not delete 'CRT_REMOVE.TXT'" );  
   else  
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );  
}  
```  
  
## <a name="input-crtremovetxt"></a>输入：crt_remove.txt  
  
```  
This file will be deleted.  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
Deleted 'CRT_REMOVE.TXT'  
```  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_unlink、_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)