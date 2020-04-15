---
title: fflush
ms.date: 4/2/2020
api_name:
- fflush
- _o_fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: 401f715e99e6304f0726c8b9c96a71d9582dbc1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347170"
---
# <a name="fflush"></a>fflush

刷新流。

## <a name="syntax"></a>语法

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

如果缓冲区已成功刷新，**则 fflush**返回 0。 在指定流无缓冲区或处于打开状态以仅供读取的情况下，也会返回值 0。 **EOF**的返回值指示错误。

> [!NOTE]
> 如果**fflush**返回**EOF，** 则数据可能由于写入失败而丢失。 设置严重错误处理程序时，使用**setvbuf**函数关闭缓冲区或使用低级 I/O 例程（如 **_open、_close**和 **_write**而不是流 I/O 函数是最安全的。 **_open**

## <a name="remarks"></a>备注

**刷新**函数刷新*流*。 如果以写入模式打开流，或者以更新模式打开并且最后一个操作是写入，则流缓冲区的内容会被写入到基础文件，否则设备和缓冲区将被丢弃。 如果在读取模式下打开流，或者如果流没有缓冲区，则对**fflush**的调用没有效果，并且保留任何缓冲区。 对**fflush**的调用会抵消之前对**流的 ungetc**的任何调用的效果。 调用后，该流保持打开状态。

如果*流*为**NULL，** 则行为与调用每个打开的流发出**相同的**行为相同。 最后一次操作是写入的所有以写入模式打开的流以及所有以更新模式打开的流都将被刷新。 调用对其他流无效。

缓冲区通常由操作系统维护，操作系统确定将数据自动写入磁盘的最佳时间：当缓冲区已满时、当流已关闭时或当程序在未关闭流的情况下正常终止时。 利用运行时库的提交到磁盘功能，可以确保将关键数据直接写入磁盘而不是操作系统的缓冲区。 无需重写现有程序，可以通过将程序的对象文件与 COMMODE.OBJ 链接来启用此功能。 在生成的可执行文件中，调用 **_flushall**将所有缓冲区的内容写入磁盘。 只有 **_flushall**和**冲洗**受COMMODE.OBJ的影响。

有关控制提交到磁盘功能的信息，请参阅[流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

此函数会锁定调用线程，因此是线程安全的。 有关非锁定版本，请参阅 **_fflush_nolock**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fflush.c
// Compile with: cl /W4 crt_fflush.c
// This sample gets a number from the user, then writes it to a file.
// It ensures the write isn't lost on crash by calling fflush.
#include <stdio.h>

int * crash_the_program = 0;

int main(void)
{
    FILE * my_file;
    errno_t err = fopen_s(&my_file, "myfile.txt", "w");
    if (my_file && !err)
    {
        printf("Write a number: ");

        int my_number = 0;
        scanf_s("%d", &my_number);

        fprintf(my_file, "User selected %d\n", my_number);

        // Write data to a file immediately instead of buffering.
        fflush(my_file);

        if (my_number == 5)
        {
            // Without using fflush, no data was written to the file
            // prior to the crash, so the data is lost.
            *crash_the_program = 5;
        }

        // Normally, fflush is not needed as closing the file will write the buffer.
        // Note that files are automatically closed and flushed during normal termination.
        fclose(my_file);
    }
    return 0;
}
```

```Input
5
```

```myfile.txt
User selected 5
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
