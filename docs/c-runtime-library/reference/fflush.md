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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c5208c86484e1d9478f3879d91b32d57ba7c4a3a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912900"
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

如果缓冲区已成功刷新， **fflush**将返回0。 在指定流无缓冲区或处于打开状态以仅供读取的情况下，也会返回值 0。 **EOF**的返回值指示一个错误。

> [!NOTE]
> 如果**fflush**返回**EOF**，则数据可能因写入失败而丢失。 设置关键错误处理程序时，最安全的方法是使用**setvbuf**函数关闭缓冲并使用低级别 i/o 例程，如 **_open**、 **_close**和 **_write** ，而不是使用流 i/o 函数。

## <a name="remarks"></a>备注

**Fflush**函数刷新流*流*。 如果以写入模式打开流，或者以更新模式打开并且最后一个操作是写入，则流缓冲区的内容会被写入到基础文件，否则设备和缓冲区将被丢弃。 如果流是在读取模式下打开的，或者如果流没有缓冲区，则对**fflush**的调用不起作用，并且保留任何缓冲区。 对**fflush**的调用会对流的**ungetc**的任何先前调用的效果求反。 调用后，该流保持打开状态。

如果*stream*为**NULL**，则行为与对每个打开的流的**fflush**的调用相同。 最后一次操作是写入的所有以写入模式打开的流以及所有以更新模式打开的流都将被刷新。 调用对其他流无效。

缓冲区通常由操作系统维护，操作系统确定将数据自动写入磁盘的最佳时间：当缓冲区已满时、当流已关闭时或当程序在未关闭流的情况下正常终止时。 利用运行时库的提交到磁盘功能，可以确保将关键数据直接写入磁盘而不是操作系统的缓冲区。 无需重写现有程序，可以通过将程序的对象文件与 COMMODE.OBJ 链接来启用此功能。 在生成的可执行文件中，调用 **_flushall**将所有缓冲区的内容写入磁盘。 只有 **_flushall**和**fflush**受 commode.obj 的影响。

有关控制提交到磁盘功能的信息，请参阅[流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

此函数会锁定调用线程，因此是线程安全的。 有关非锁定版本，请参阅 **_fflush_nolock**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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
