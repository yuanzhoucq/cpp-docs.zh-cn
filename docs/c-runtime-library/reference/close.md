---
title: _close
ms.date: 11/04/2016
apiname:
- _close
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
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: faea008903136e8abdc39297672b31800ada796d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528019"
---
# <a name="close"></a>_close

关闭文件。

## <a name="syntax"></a>语法

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>参数

*fd*<br/>
引用打开的文件的文件说明符。

## <a name="return-value"></a>返回值

**_close**如果已成功关闭文件，则返回 0。 返回值-1 指示错误。

## <a name="remarks"></a>备注

**_Close**函数将关闭与关联的文件*fd*。

文件描述符和基础 OS 文件句柄已关闭。 因此，不需要调用**CloseHandle**如果最初使用 Win32 函数打开该文件**CreateFile**并转换为文件描述符使用 **_open_osfhandle**.

此函数验证其参数。 如果*fd*是错误的文件描述符，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，该函数将返回-1 和**errno**设置为**EBADF**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_open](open-wopen.md) 示例。

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_unlink、_wunlink](unlink-wunlink.md)<br/>
