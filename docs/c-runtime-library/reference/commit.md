---
title: _commit | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e9bc746c347bfb60fb78edbf025b676f8218c66
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394826"
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

**_commit**返回 0，如果该文件已成功刷新并保存到磁盘。 返回值-1 指示错误。

## <a name="remarks"></a>备注

**_Commit**函数强制写入与关联的文件的操作系统*fd*到磁盘。 此调用可确保立即刷新特定文件，而无需等待操作系统的决定。

如果*fd*不是无效的文件描述符，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回-1 和**errno**设置为**EBADF**。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>
