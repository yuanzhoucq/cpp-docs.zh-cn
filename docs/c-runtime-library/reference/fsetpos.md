---
title: fsetpos | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fsetpos
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
- fsetpos
dev_langs:
- C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c381cf478a97d47efe10c68096fffe3d9fd8efdf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fsetpos"></a>fsetpos

设置流位置指示器。

## <a name="syntax"></a>语法

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

*pos*<br/>
位置指示器存储。

## <a name="return-value"></a>返回值

如果成功， **fsetpos**返回 0。 在失败时，该函数返回非零值，并将设置**errno**下列其中一清单常量 （在 ERRNO 中定义。H): **EBADF**，这意味着文件不可访问或该对象的*流*指向不是有效的文件结构; 或**EINVAL**，这意味着的值无效*流*或*pos*传递。 如果传入了无效参数，这些函数则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Fsetpos**函数设置的文件位置指示器*流*为的值*pos*，这在调用中获取**fgetpos**针对*流*。 该函数清除文件尾指示器和撤消的任何影响[ungetc](ungetc-ungetwc.md)上*流*。 在调用**fsetpos**上的下一步操作*流*可能被输入或输出。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [fgetpos](fgetpos.md) 的示例。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
