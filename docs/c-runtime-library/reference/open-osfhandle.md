---
title: _open_osfhandle
ms.date: 05/21/2019
apiname:
- _open_osfhandle
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
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 8527dade37f20b7341d5a26f5752ece668ab7fc9
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174804"
---
# <a name="openosfhandle"></a>_open_osfhandle

将 C 运行时文件描述符与现有操作系统文件句柄关联。

## <a name="syntax"></a>语法

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>参数

*osfhandle*<br/>
操作系统文件句柄。

*flags*<br/>
允许的操作类型。

## <a name="return-value"></a>返回值

如果成功，**_open_osfhandle** 返回 C 运行时文件描述符。 否则返回 -1。

## <a name="remarks"></a>备注

_open_osfhandle 函数分配 C 运行时文件描述符，并将其与由 osfhandle 指定的操作系统文件句柄相关联。 要避免编译器警告，请将 osfhandle 参数强制转换为 intptr_t。 flags 参数是一个整数表达式，是由在 \<fcntl.h> 中定义的一个或多个清单常量组合构成。 当使用两个或多个清单常量来形成 flags 参数时，这些常量将与按位 OR 运算符 (&#124;) 合并。

清单常量在 \<fcntl.h>: 中定义

|||
|-|-|
| \_O\_APPEND | 在执行每个写入操作之前，将文件指针定位到文件结尾。 |
| \_O\_RDONLY | 打开文件以供只读。 |
| \_O\_TEXT | 在文本（转换）模式下打开文件。 |
| \_O\_WTEXT | 在 Unicode（转换 UTF-16）模式下打开文件。 |

_open_osfhandle 调用将 Win32 文件句柄的所有权转移给文件描述符。 要使用- _open_osfhandle 关闭已打开的文件，请调用 [\_close](close.md)。 底层 OS 文件句柄也由对 _close 的调用关闭。 请勿对原始句柄调用 Win32 函数 CloseHandle。 如果文件描述符由 FILE &#42; 流拥有，则 FILE &#42; 流上的对 [fclose](fclose-fcloseall.md) 的调用会关闭文件描述符和底层句柄。 在此情况下，请勿在文件描述符上调用 _close，或在原始句柄上调用 CloseHandle。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
