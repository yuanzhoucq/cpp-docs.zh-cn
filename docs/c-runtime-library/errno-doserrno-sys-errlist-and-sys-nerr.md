---
title: errno、_doserrno、_sys_errlist 和 _sys_nerr
ms.date: 11/04/2016
api_name:
- _errno
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sys_errlist
- errno
- _sys_nerr
- _doserrno
helpviewer_keywords:
- error codes, printing
- sys_errlist global variable
- doserrno global variable
- errno global variable
- _doserrno global variable
- _sys_errlist global variable
- _sys_nerr global variable
- sys_nerr global variable
ms.assetid: adbec641-6d91-4e19-8398-9a34046bd369
ms.openlocfilehash: 5b10d98dab41151290d4e44e031f659108b0c73c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944559"
---
# <a name="errno-_doserrno-_sys_errlist-and-_sys_nerr"></a>errno、_doserrno、_sys_errlist 和 _sys_nerr

在程序执行过程中设置的保存错误代码的全局宏，以及用于显示的错误代码的等效字符串。

## <a name="syntax"></a>语法

```
#define errno   (*_errno())
#define _doserrno   (*__doserrno())
#define _sys_errlist (__sys_errlist())
#define _sys_nerr (*__sys_nerr())
```

## <a name="remarks"></a>备注

程序启动期间，`errno` 和 `_doserrno` 均由运行时设置为 0。 `errno` 是在系统级调用中发生错误时设置的。 由于 `errno` 保留设置它的上一次调用的值，因此该值可能会被后续的调用更改。 发生错误时设置 `errno` 的运行库调用不会在成功后清除 `errno`。 始终在调用可能设置 `errno` 前，通过调用 `_set_errno(0)` 立即清除它，并在调用后立即进行检查。

发生错误时，`errno` 不必设置为与系统调用返回的错误代码相同的值。 对于 I/O 操作，`_doserrno` 将存储与 `errno` 代码等效的操作系统错误代码。 对于大多数非 I/O 操作，未设置 `_doserrno` 的值。

每个 `errno` 值都与可通过使用一个 [perror](../c-runtime-library/reference/perror-wperror.md) 函数输出的 `_sys_errlist` 中的错误消息相关联，或者通过使用一个 [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) 或 [strerror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) 函数存储在字符串中。 `perror` 和 `strerror` 函数使用 `_sys_errlist` 数组和 `_sys_nerr`（`_sys_errlist` 中的元素数量）处理错误信息。 出于代码安全原因，已弃用对 `_sys_errlist` 和 `_sys_nerr` 的直接访问。 我们建议你使用更安全的函数版本，而非全局宏，如下所示：

|全局宏|等效函数|
|------------------|----------------------------|
|`_doserrno`|[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)、[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)|
|`errno`|[_get_errno](../c-runtime-library/reference/get-errno.md)、[_set_errno](../c-runtime-library/reference/set-errno.md)|
|`_sys_errlist`， `_sys_nerr`|[strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|

库数学例程通过调用 [_matherr](../c-runtime-library/reference/matherr.md) 设置 `errno`。 若要以不同方式处理数学错误，请根据 `_matherr` 引用说明编写你自己的例程，并将其命名为 `_matherr`。

下表中的所有 `errno` 值是在 \<errno.h> 中预定义的常量，并且与 UNIX 兼容。 ISO C99 标准中仅指定了 `ERANGE`、`EILSEQ` 和 `EDOM`。

|返回的常量|系统错误消息|值|
|--------------|--------------------------|-----------|
|`EPERM`|不允许执行该操作|1|
|`ENOENT`|没有此文件或目录|2|
|`ESRCH`|没有此进程|3|
|`EINTR`|函数中断|4|
|`EIO`|I/O 错误|5|
|`ENXIO`|没有此设备或地址|6|
|`E2BIG`|参数列表太长|7|
|`ENOEXEC`|执行格式错误|8|
|`EBADF`|文件编号错误|9|
|`ECHILD`|没有生成的进程|10|
|`EAGAIN`|没有更多进程、没有足够内存或达到最大嵌套级别|11|
|`ENOMEM`|没有足够内存|12|
|`EACCES`|权限被拒绝|13|
|`EFAULT`|地址错误|14|
|`EBUSY`|设备或资源忙碌|16|
|`EEXIST`|文件已存在|17|
|`EXDEV`|跨设备链接|18|
|`ENODEV`|没有此设备|19|
|`ENOTDIR`|不是目录|20|
|`EISDIR`|是目录|21|
|`EINVAL`|参数无效|22|
|`ENFILE`|系统中打开的文件太多|23|
|`EMFILE`|打开的文件太多|24|
|`ENOTTY`|不适当的 I/O 控制操作|25|
|`EFBIG`|文件太大|27|
|`ENOSPC`|设备上没有剩余空间|28|
|`ESPIPE`|搜寻无效|29|
|`EROFS`|只读文件系统|30|
|`EMLINK`|链接太多|31|
|`EPIPE`|管道损坏|32|
|`EDOM`|数学参数|33|
|`ERANGE`|结果太大|34|
|`EDEADLK`|会发生资源死锁|36|
|`EDEADLOCK`|与 EDEADLK 相同，以便与早期的 Microsoft C 版本兼容|36|
|`ENAMETOOLONG`|文件名太长|38|
|`ENOLCK`|无可用锁|39|
|`ENOSYS`|函数不受支持|40|
|`ENOTEMPTY`|目录不为空|41|
|`EILSEQ`|非法字节序列|42|
|`STRUNCATE`|字符串被截断|80|

## <a name="requirements"></a>要求

|全局宏|必需的标头|可选标头|
|------------------|---------------------|---------------------|
|`errno`|\<errno.h> 或 \<stdlib.h>，\<cerrno> 或 \<cstdlib> (C++)||
|`_doserrno`, `_sys_errlist`, `_sys_nerr`|\<stdlib.h>、\<cstdlib> (C++)|\<errno.h>、\<cerrno> (C++)|

`_doserrno`、`_sys_errlist` 和 `_sys_nerr` 宏是 Microsoft 扩展。 有关更多兼容性信息，请参阅 [兼容性](../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[全局变量](../c-runtime-library/global-variables.md)<br/>
[errno 常量](../c-runtime-library/errno-constants.md)<br/>
[perror、_wperror](../c-runtime-library/reference/perror-wperror.md)<br/>
[strerror、_strerror、_wcserror、\__wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)<br/>
[strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)<br/>
[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)<br/>
[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)<br/>
[_get_errno](../c-runtime-library/reference/get-errno.md)<br/>
[_set_errno](../c-runtime-library/reference/set-errno.md)
