---
title: "_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _findfirst
- _wfindfirst
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
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
dev_langs:
- C++
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73e513cf4e1d63888f9ad6ef12ed6532b7e158ef
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64
提供与 `filespec` 参数中指定的文件匹配的文件名的第一个实例的有关信息。  
  
## <a name="syntax"></a>语法  
  
```  
intptr_t _findfirst(  
   const char *filespec,  
   struct _finddata_t *fileinfo   
);  
intptr_t _findfirst32(  
   const char *filespec,  
   struct _finddata32_t *fileinfo   
);  
intptr_t _findfirst64(  
   const char *filespec,  
   struct _finddata64_t *fileinfo   
);  
intptr_t _findfirsti64(  
   const char *filespec,  
   struct _finddatai64_t *fileinfo   
);  
intptr_t _findfirst32i64(  
   const char *filespec,  
   struct _finddata32i64_t *fileinfo   
);  
intptr_t _findfirst64i32(  
   const char *filespec,  
   struct _finddata64i32_t *fileinfo   
);  
intptr_t _wfindfirst(  
   const wchar_t *filespec,  
   struct _wfinddata_t *fileinfo   
);  
intptr_t _wfindfirst32(  
   const wchar_t *filespec,  
   struct _wfinddata32_t *fileinfo   
);  
intptr_t _wfindfirst64(  
   const wchar_t *filespec,  
   struct _wfinddata64_t *fileinfo   
);  
intptr_t _wfindfirsti64(  
   const wchar_t *filespec,  
   struct _wfinddatai64_t *fileinfo   
);  
intptr_t _wfindfirst32i64(  
   const wchar_t *filespec,  
   struct _wfinddata32i64_t *fileinfo   
);  
intptr_t _wfindfirst64i32(  
   const wchar_t *filespec,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### <a name="parameters"></a>参数  
 `filespec`  
 目标文件规范（可以包含通配符）。  
  
 `fileinfo`  
 文件信息缓冲区。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `_findfirst` 返回标识与 `filespec` 规范匹配的文件或文件组的唯一搜索句柄，可在后续调用 [_findnext](../../c-runtime-library/reference/findnext-functions.md) 或 `_findclose` 时使用。 否则为`_findfirst`返回-1 并设置`errno`为以下值之一。  
  
 `EINVAL`  
 无效参数：`filespec` 或 `fileinfo` 为 `NULL`。 或者，操作系统返回了意外错误。  
  
 `ENOENT`  
 无法匹配的文件规范。  
  
 `ENOMEM`  
 内存不足。  
  
 `EINVAL`  
 文件名规范无效或指定的文件名大于 `MAX_PATH`。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果传入了无效参数，这些函数则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
## <a name="remarks"></a>备注  
 完成 `_findfirst` 或 `_findnext` 函数后（或任何变量），必须调用 [_findclose](../../c-runtime-library/reference/findclose.md)。 这将释放应用程序中这些函数所使用的资源。  
  
 这些具有 `w` 前缀的函数的变体都是宽字符版本；否则，它们与相应的单字节函数完全相同。  
  
 这些函数的变体支持 32 位或 64 位时间类型以及 32 位或 64 位文件大小。 第一个数字后缀（`32` 或 `64`）表示时间类型的大小；第二个后缀是 `i32` 或 `i64`，表示以 32 位还是 64 位整数表示文件大小。 有关支持 32 位和 64 位时间类型及文件大小的版本的信息，请参阅下表。 如果与时间类型的大小相同，则省略 `i32` 或 `i64` 后缀，因此 `_findfirst64` 还支持 64 位文件长度，而 `_findfirst32` 仅支持 32 位文件长度。  
  
 这些函数将各种形式的 `_finddata_t` 结构用于 `fileinfo` 参数。 有关结构的详细信息，请参阅[文件名搜索函数](../../c-runtime-library/filename-search-functions.md)。  
  
 使用 64 位时间类型的变体允许文件创建日期最大表示为 3000 年 12 月 31 日 23:59:59，UTC。 那些使用 32 位时间类型的变体只能表示截至 2038 年 1 月 18 日 23:59:59，UTC 之前的日期。 1970 年 1 月 1 日午夜是所有这些函数的日期范围下限。  
  
 除非有特定原因要使用显式指定时间大小的版本，否则请使用 `_findfirst` 或 `_wfindfirst`；如果需要支持大于 3 GB 的文件大小，请使用 `_findfirsti64` 或 `_wfindfirsti64`。 所有这些函数均使用 64 位时间类型。 在早期版本中，这些函数使用 32 位时间类型。 如果这是某个应用程序的一项重大更改，可以定义 `_USE_32BIT_TIME_T` 以还原为旧行为。 如果已定义 `_USE_32BIT_TIME_T`，则 `_findfirst`、`_finfirsti64` 及其对应的 Unicode 版本将使用 32 位时间。  
  
### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>_findfirst 的时间类型和文件长度类型变体  
  
|函数|已定义 `_USE_32BIT_TIME_T`？|时间类型|文件长度类型|  
|---------------|----------------------------------|---------------|----------------------|  
|`_findfirst`, `_wfindfirst`|未定义|64 位|32 位|  
|`_findfirst`, `_wfindfirst`|已定义|32 位|32 位|  
|`_findfirst32`, `_wfindfirst32`|不受宏定义影响|32 位|32 位|  
|`_findfirst64`, `_wfindfirst64`|不受宏定义影响|64 位|64 位|  
|`_findfirsti64`, `_wfindfirsti64`|未定义|64 位|64 位|  
|`_findfirsti64`, `_wfindfirsti64`|已定义|32 位|64 位|  
|`_findfirst32i64`, `_wfindfirst32i64`|不受宏定义影响|32 位|64 位|  
|`_findfirst64i32`, `_wfindfirst64i32`|不受宏定义影响|64 位|32 位|  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfindfirst`|`_findfirst`|`_findfirst`|`_wfindfirst`|  
|`_tfindfirst32`|`_findfirst32`|`_findfirst32`|`_wfindfirst32`|  
|`_tfindfirst64`|`_findfirst64`|`_findfirst64`|`_wfindfirst64`|  
|`_tfindfirsti64`|`_findfirsti64`|`_findfirsti64`|`_wfindfirsti64`|  
|`_tfindfirst32i64`|`_findfirst32i64`|`_findfirst32i64`|`_wfindfirst32i64`|  
|`_tfindfirst64i32`|`_findfirst64i32`|`_findfirst64i32`|`_wfindfirst64i32`|  
  
## <a name="requirements"></a>惠?  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_findfirst`|\<io.h>|  
|`_findfirst32`|\<io.h>|  
|`_findfirst64`|\<io.h>|  
|`_findfirsti64`|\<io.h>|  
|`_findfirst32i64`|\<io.h>|  
|`_findfirst64i32`|\<io.h>|  
|`_wfindfirst`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirst32`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirst64`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirsti64`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirst32i64`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirst64i32`|\<io.h> 或 \<wchar.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [系统调用](../../c-runtime-library/system-calls.md)   
 [文件名搜索函数](../../c-runtime-library/filename-search-functions.md)