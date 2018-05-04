---
title: ferror | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ferror
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
- ferror
dev_langs:
- C++
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49aaff776a90dd687ee4dae1902903ed01b83e20
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ferror"></a>ferror

测试流中的错误。

## <a name="syntax"></a>语法

```C
int ferror(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

如果不发生任何错误*流*， **ferror**返回 0。 否则，返回一个非零值。 如果流是**NULL**， **ferror**中所述调用无效参数处理程序，[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将**errno**到**EINVAL**并返回 0。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Ferror**的读取或写入错误，与关联的文件的例程 （同时作为函数和宏实现） 测试*流*。 如果出现错误，直到流已关闭或回退，或直到将保持设置为流的错误指示器**clearerr**针对其调用。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**ferror**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [feof](feof.md) 的示例。

## <a name="see-also"></a>请参阅

[错误处理](../../c-runtime-library/error-handling-crt.md)<br/>
[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
