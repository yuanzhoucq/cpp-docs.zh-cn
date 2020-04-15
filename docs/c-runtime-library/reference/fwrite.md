---
title: fwrite
ms.date: 4/2/2020
api_name:
- fwrite
- _o_fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: a5bd6da3c8d16189f7ff0db744901e03513acc21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345395"
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

*缓冲区*<br/>
指向要写入的数据的指针。

*大小*<br/>
项大小（以字节为单位）。

*count*<br/>
要写入的项的最大数量。

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**fwrite**返回实际写入的完整项数，如果发生错误，该项可能小于*计数*。 此外，如果发生错误，则无法确定文件位置指示器。 如果*流*或*缓冲区*是空指针，或者如果在 Unicode 模式下指定了奇数的字节，则函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，此函数将**errno**设置到**EINVAL**并返回 0。

## <a name="remarks"></a>备注

**fwrite**函数写入*以计算*从*缓冲区*到输出*流*的项，每个*项的大小*长度。 与*流*关联的文件指针（如果有）将递增为实际写入的字节数。 如果在文本模式下打开*流*，则每个换行符将替换为回车换行对。 该替换不会影响返回值。

在 Unicode 转换模式下打开*流*时（例如，如果通过调用**fopen**并使用包含 ccs_UNICODE、ccs_UTF-16LE**ccs=UNICODE**或**ccs_UTF-8**的模式参数）打开*流*，或者通过使用 **_setmode**和**ccs=UTF-16LE**包含 **_O_WTEXT、_O_U16TEXT**或 **_O_U8TEXT***缓冲区*的模式参数将模式更改为包含 UTF-16 的**wchar_t**数组的指针。 **_O_U16TEXT** 尝试在此模式下写入奇数个字节会导致参数验证错误。

因为此函数会锁定调用线程，因此它是线程安全的。 有关非锁定版本，请参阅 **_fwrite_nolock**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [fread](fread.md) 示例。

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
