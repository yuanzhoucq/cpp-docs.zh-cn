---
title: _open_osfhandle
ms.date: 05/21/2019
api_name:
- _open_osfhandle
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 2fa2d8190082967d14dd780aa9be7286996b1f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951209"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

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

如果成功， **_open_osfhandle** 返回 C 运行时文件描述符。 否则返回 -1。

## <a name="remarks"></a>备注

**_Open_osfhandle**函数分配 C 运行时文件描述符。 它将此文件描述符与*osfhandle*指定的操作系统文件句柄关联。 要避免编译器警告，请将 osfhandle 参数强制转换为 intptr_t。 flags参数是一个整数表达式，是由在 \<fcntl.h> 中定义的一个或多个清单常量组合构成。 您可以使用按位 "或" 运算符 **&#124;** （）来合并两个或更多个清单常量以构成*flags*参数。

清单常量在 \<fcntl.h>: 中定义

|||
|-|-|
| \_O\_APPEND | 在执行每个写入操作之前，将文件指针定位到文件结尾。 |
| \_O\_RDONLY | 打开文件以供只读。 |
| \_O\_TEXT | 在文本（转换）模式下打开文件。 |
| \_O\_WTEXT | 在 Unicode（转换 UTF-16）模式下打开文件。 |

_open_osfhandle 调用将 Win32 文件句柄的所有权转移给文件描述符。 要使用- _open_osfhandle 关闭已打开的文件，请调用 [\_close](close.md)。 底层 OS 文件句柄也由对 _close 的调用关闭。 请勿对原始句柄调用 Win32 函数 CloseHandle。 如果文件描述符由**文件&#42;** 流所有，则对[fclose](fclose-fcloseall.md)的调用将关闭文件说明符和基础句柄。 在此情况下，请勿在文件描述符上调用 _close，或在原始句柄上调用 CloseHandle。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
