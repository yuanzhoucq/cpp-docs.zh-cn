---
title: _chsize_s
ms.date: 4/2/2020
api_name:
- _chsize_s
- _o__chsize_s
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: 70845124eb889d73a0f87aadd923e2d86db96c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350072"
---
# <a name="_chsize_s"></a>_chsize_s

更改文件大小。 这是 [_chsize](chsize.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>参数

*Fd*<br/>
引用打开的文件的文件描述符。

*大小*<br/>
文件的新长度（以字节为单位）。

## <a name="return-value"></a>返回值

如果文件大小已成功更改 **，_chsize_s**返回值 0。 非零返回值表示错误：如果指定文件针对访问锁定，则返回值为**EACCES;** 如果指定的文件为只读或描述符无效，则返回值为 EACCES;如果**设备上**没有空间，则返回值为 EINVAL;如果大小小于零，则返回值为**EINVAL。** **EBADF** **errno**设置为相同的值。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_chsize_s**函数将与*fd*关联的文件扩展或截截到*大小*指定的长度。 必须在允许写入的模式下打开文件。 如果扩展该文件，将追加 Null 字符 ('\0')。 如果文件被截断，则从缩短的文件的末尾到文件原始长度的所有数据都将丢失。

**_chsize_s**以 64 位整数作为文件大小，因此可以处理大于 4 GB 的文件大小。 **_chsize**限制为 32 位文件大小。

此函数验证其参数。 如果*fd*不是有效的文件描述符，或者大小小于零，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
