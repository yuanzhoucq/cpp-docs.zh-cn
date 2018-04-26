---
title: _findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wfindnext
- _findnext
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
- findnext
- _wfindnext32i64
- _tfindnext64i32
- findnext32
- findnext32i64
- wfindnext64i32
- _wfindnext
- tfindnext64
- findnexti64
- _findnexti64
- _tfindnexti64
- _findnext64i32
- tfindnexti64
- tfindnext32
- _wfindnext64i32
- findnext64i32
- _findnext
- _tfindnext32i64
- _wfindnext64
- wfindnext
- wfindnext32
- tfindnext32i64
- _findnext64
- _tfindnext64
- _wfindnext32
- findnext64
- _findnext32i64
- tfindnext
- wfindnexti64
- tfindnext64i32
- _tfindnext32
- wfindnext32i64
- wfindnext64
- _wfindnexti64
- _tfindnext
- _findnext32
dev_langs:
- C++
helpviewer_keywords:
- _wfindnexti64 function
- _tfindnext32 function
- wfindnexti64 function
- _wfindnext32i64 function
- findnext32i64 function
- tfindnext64i32 function
- _tfindnext64i32 function
- _findnext function
- findnext64i32 function
- _tfindnext function
- findnext32 function
- tfindnext32 function
- _findnext32 function
- _tfindnext32i64 function
- _wfindnext function
- tfindnext function
- _findnext64 function
- findnext64 function
- _findnext64i32 function
- wfindnext32i64 function
- findnext function
- wfindnext32 function
- _wfindnext64i32 function
- findnexti64 function
- _wfindnext64 function
- _findnext32i64 function
- _findnexti64 function
- _tfindnext64 function
- wfindnext64i32 function
- tfindnexti64 function
- wfindnext64 function
- wfindnext function
- tfindnext64 function
- _wfindnext32 function
- tfindnext32i64 function
- _tfindnexti64 function
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65947ef5d8c1cb70e587ae739a7301cbed453448
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="findnext-findnext32-findnext32i64-findnext64-findnext64i32-findnexti64-wfindnext-wfindnext32-wfindnext32i64-wfindnext64-wfindnext64i32-wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

查找下一个名称，如果有匹配*filespec*中的以前调用参数[_findfirst](findfirst-functions.md)，然后更改*fileinfo*相应地结构内容。

## <a name="syntax"></a>语法

```C
int _findnext(
   intptr_t handle,
   struct _finddata_t *fileinfo
);
int _findnext32(
   intptr_t handle,
   struct _finddata32_t *fileinfo
);
int _findnext64(
   intptr_t handle,
   struct __finddata64_t *fileinfo
);
int _findnexti64(
   intptr_t handle,
   struct __finddatai64_t *fileinfo
);
int _findnext32i64(
   intptr_t handle,
   struct _finddata32i64_t *fileinfo
);
int _findnext64i32(
   intptr_t handle,
   struct _finddata64i32_t *fileinfo
);
int _wfindnext(
   intptr_t handle,
   struct _wfinddata_t *fileinfo
);
int _wfindnext32(
   intptr_t handle,
   struct _wfinddata32_t *fileinfo
);
int _wfindnext64(
   intptr_t handle,
   struct _wfinddata64_t *fileinfo
);
int _wfindnexti64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext32i64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext64i32(
   intptr_t handle,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>参数

*句柄*<br/>
通过上次调用返回的搜索句柄 **_findfirst**。

*fileinfo*<br/>
文件信息缓冲区。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 否则为返回-1 并设置**errno**到一个值，该值故障的性质。 下表中显示了可能的错误代码。

|errno 值|条件|
|-|-|
**EINVAL**|无效的参数： *fileinfo*已**NULL**。 或者，操作系统返回了意外错误。
**ENOENT**|找不到更多匹配的文件。
**ENOMEM**|没有足够的内存或文件名称的长度超过**MAX_PATH**。

如果传入了无效参数，这些函数则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

## <a name="remarks"></a>备注

必须调用[_findclose](findclose.md)在完成使用后 **_findfirst**或 **_findnext**函数 （或任何变体）。 这将释放应用程序中这些函数所使用的资源。

使用这些函数的变体**w**前缀都是宽字符版本; 否则，它们为与相应的单字节函数相同。

这些函数的变体支持 32 位或 64 位时间类型以及 32 位或 64 位文件大小。 第一个数字后缀 (**32**或**64**) 指示时间的大小使用类型; 第二个后缀是**i32**或**i64**，指示是否将文件大小表示为一个 32 位或 64 位整数。 有关支持 32 位和 64 位时间类型及文件大小的版本的信息，请参阅下表。 使用 64 位时间类型的变体允许文件创建日期最大表示为 3000 年 12 月 31 日 23:59:59，UTC；那些使用 32 位时间类型的变体只能表示截至 2038 年 1 月 18 日 23:59:59，UTC 之前的日期。 1970 年 1 月 1 日午夜是所有这些函数的日期范围下限。

除非有特定原因要使用的版本显式指定的时间大小，请使用 **_findnext**或 **_wfindnext**或者，如果你需要支持文件大小超过 3 GB，使用 **_findnexti64**或 **_wfindnexti64**。 所有这些函数均使用 64 位时间类型。 在早期版本中，这些函数使用 32 位时间类型。 如果这是一项重大更改为应用程序，你可以定义 **_USE_32BIT_TIME_T**若要获取这一旧行为。 如果 **_USE_32BIT_TIME_T**定义， **_findnext**， **_finnexti64**和其相应的 Unicode 版本使用 32 位时间。

### <a name="time-type-and-file-length-type-variations-of-findnext"></a>_findnext 的时间类型和文件长度类型变体

|函数|**_USE_32BIT_TIME_T**定义？|时间类型|文件长度类型|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**， **_wfindnext**|未定义|64 位|32 位|
|**_findnext**， **_wfindnext**|已定义|32 位|32 位|
|**_findnext32**， **_wfindnext32**|不受宏定义影响|32 位|32 位|
|**_findnext64**， **_wfindnext64**|不受宏定义影响|64 位|64 位|
|**_findnexti64**， **_wfindnexti64**|未定义|64 位|64 位|
|**_findnexti64**， **_wfindnexti64**|已定义|32 位|64 位|
|**_findnext32i64**， **_wfindnext32i64**|不受宏定义影响|32 位|64 位|
|**_findnext64i32**， **_wfindnext64i32**|不受宏定义影响|64 位|32 位|

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<io.h> 或 \<wchar.h>|
|**_wfindnext32**|\<io.h> 或 \<wchar.h>|
|**_wfindnext64**|\<io.h> 或 \<wchar.h>|
|**_wfindnexti64**|\<io.h> 或 \<wchar.h>|
|**_wfindnext32i64**|\<io.h> 或 \<wchar.h>|
|**_wfindnext64i32**|\<io.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[系统调用](../../c-runtime-library/system-calls.md)<br/>
[文件名搜索函数](../../c-runtime-library/filename-search-functions.md)<br/>
