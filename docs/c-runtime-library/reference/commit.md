---
title: _commit
ms.date: 11/04/2016
apiname:
- _commit
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
- _commit
- commit
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
ms.openlocfilehash: 8408158cb3d4ef0d29d9af24d8a2acbd28e00192
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523062"
---
# <a name="commit"></a>_commit

将文件直接刷新到磁盘。

## <a name="syntax"></a>语法

```C
int _commit(
   int fd
);
```

### <a name="parameters"></a>参数

*fd*<br/>
引用打开的文件的文件说明符。

## <a name="return-value"></a>返回值

**_commit**返回 0，如果文件已成功刷新到磁盘。 返回值-1 指示错误。

## <a name="remarks"></a>备注

**_Commit**函数强制操作系统编写与关联的文件*fd*到磁盘。 此调用可确保立即刷新特定文件，而无需等待操作系统的决定。

如果*fd*是一个无效文件说明符，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，该函数返回-1 和**errno**设置为**EBADF**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>
