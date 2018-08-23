---
title: fwrite | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fwrite
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
- fwrite
dev_langs:
- C++
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1320bcc61830833f2b1a4a225dff30652df2d3a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400575"
---
# <a name="fwrite"></a>fwrite

将数据写入流。

## <a name="syntax"></a>语法

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>参数

*buffer*<br/>
指向要写入的数据的指针。

*size*<br/>
项大小（以字节为单位）。

*count*<br/>
要写入的项的最大数量。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fwrite**返回完整的数目实际写入的项，这可能会小于*计数*如果发生错误。 此外，如果发生错误，则无法确定文件位置指示器。 如果任一*流*或*缓冲区*是 null 指针，或如果在 Unicode 模式下指定了奇数个字节写入，则函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将**errno**到**EINVAL**并返回 0。

## <a name="remarks"></a>备注

**Fwrite**函数最多写入*计数*项的*大小*长度每个，从*缓冲区*到输出*流*. 与关联的文件指针*流*（如果有） 就会递增的实际写入的字节数。 如果*流*打开在文本模式下，每个换行符替换为回车符-换行符对。 该替换不会影响返回值。

当*流*在 Unicode 转换模式下打开 — 例如，如果*流*打开通过调用**fopen**和使用模式参数，其中包含**ccs= UNICODE**， **ccs = UTF 16LE**，或**ccs = utf-8**，或如果模式更改为 Unicode 转换模式使用 **_setmode**和模式参数，其中包含 **_O_WTEXT**， **_O_U16TEXT**，或 **_O_U8TEXT**-*缓冲区*解释为指向的指针数组**wchar_t**包含 utf-16 数据。 尝试在此模式下写入奇数个字节会导致参数验证错误。

因为此函数会锁定调用线程，因此它是线程安全的。 有关非锁定版本，请参阅 **_fwrite_nolock**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [fread](fread.md) 示例。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
