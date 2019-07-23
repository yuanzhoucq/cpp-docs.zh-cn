---
title: fwrite
ms.date: 11/04/2016
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
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: f05e39390f3a2d0ad41627f6aed1aecd77b57cca
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376062"
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

*计数*<br/>
要写入的项的最大数量。

*stream*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fwrite**返回实际写入的完整项的数量, 如果发生错误, 则可能小于*计数*。 此外，如果发生错误，则无法确定文件位置指示器。 如果*流*或*缓冲区*为空指针, 或者如果在 Unicode 模式下指定了要写入的奇数个字节, 则函数将调用无效参数处理程序, 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则此函数会将**errno**设置为**EINVAL** , 并返回0。

## <a name="remarks"></a>备注

**Fwrite**函数将每个项的*大小*从*缓冲区*写入到输出*流*, 并对其进行*计算*。 与*流*关联的文件指针 (如果有) 以实际写入的字节数为增量递增。 如果在文本模式下打开*流*, 则会将每个换行符替换为回车换行符对。 该替换不会影响返回值。

在 Unicode 转换模式下打开*流*时 (例如, 如果通过调用**fopen**打开*流*, 并使用包含**ccs = Unicode**、 **ccs = utf-utf-16le**或**ccs = utf-8**的模式参数), 或者如果模式为, 则为通过使用 **_setmode**和包含 **_O_WTEXT**、 **_O_U16TEXT**或 **_O_U8TEXT**的模式参数更改为 Unicode 转换模式,*缓冲区*被解释为指向包含  UTF-16 数据。 尝试在此模式下写入奇数个字节会导致参数验证错误。

因为此函数会锁定调用线程，因此它是线程安全的。 有关非锁定版本, 请参阅 **_fwrite_nolock**。

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
