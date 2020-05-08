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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: faed95bfeb6fad88f502101e166ec6124b6e591d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910415"
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

*fd*<br/>
引用打开的文件的文件描述符。

size <br/>
文件的新长度（以字节为单位）。

## <a name="return-value"></a>返回值

如果文件大小已成功更改， **_chsize_s**返回值0。 非零返回值指示错误：如果指定的文件是只读的，则返回值为**EACCES** ; 如果指定的文件是只读的或描述符无效 **，则为**ENOSPC; 如果设备上没有剩余空间，则返回**ENOSPC** ; 如果 Size 小于零，则返回**EINVAL** 。 **errno**设置为相同的值。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Chsize_s**函数将与*fd*关联的文件扩展或截断为*大小*指定的长度。 必须在允许写入的模式下打开文件。 如果扩展该文件，将追加 Null 字符 ('\0')。 如果文件被截断，则从缩短的文件的末尾到文件原始长度的所有数据都将丢失。

**_chsize_s**采用64位整数作为文件大小，因此可以处理大于 4 GB 的文件大小。 **_chsize**限制为32位文件大小。

此函数验证其参数。 如果*fd*不是有效的文件描述符或大小小于零，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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
