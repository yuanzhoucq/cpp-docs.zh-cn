---
title: _chsize_s
ms.date: 11/04/2016
apiname:
- _chsize_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: a56efe826d43c80dc2cdee295e58872e7dd3c9ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597595"
---
# <a name="chsizes"></a>_chsize_s

更改文件大小。 这是 [_chsize](chsize.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>参数

*fd*<br/>
引用打开的文件的文件描述符。

*size*<br/>
文件的新长度（以字节为单位）。

## <a name="return-value"></a>返回值

**_chsize_s**如果已成功更改文件大小，则返回值 0。 非零返回值指示错误： 返回值是**EACCES**如果指定的文件针对访问权限，锁定**EBADF**如果指定的文件是只读的或者该描述符无效**ENOSPC**如果没有空间保留在设备上，或**EINVAL**如果大小小于零。 **errno**设置为相同的值。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Chsize_s**函数扩展或截断与关联的文件*fd*到指定的长度*大小*。 必须在允许写入的模式下打开文件。 如果扩展该文件，将追加 Null 字符 ('\0')。 如果文件被截断，则从缩短的文件的末尾到文件原始长度的所有数据都将丢失。

**_chsize_s**采用 64 位整数作为文件大小，并因此可以处理大于 4 GB 文件大小。 **_chsize**被限制为 32 位文件大小。

此函数验证其参数。 如果*fd*不是有效的文件描述符或大小小于零，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
