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
ms.openlocfilehash: 9e940844eb5e37755c10999feb294981afc8683a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821595"
---
# <a name="openosfhandle"></a>_open_osfhandle

将 C 运行时文件描述符与现有的操作系统文件句柄相关联。

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

**_Open_osfhandle**函数分配 C 运行时文件描述符。 它将此文件描述符与由指定的操作系统文件句柄相关联*osfhandle*。 要避免编译器警告，请将 osfhandle 参数强制转换为 intptr_t    。 flags  参数是一个整数表达式，是由在 \<fcntl.h> 中定义的一个或多个清单常量组合构成。 可以使用按位 OR 运算符 ( **&#124;** ) 合并到窗体的两个或多个清单常量*标志*自变量。

清单常量在 \<fcntl.h>: 中定义

|||
|-|-|
| \_O\_APPEND  | 在执行每个写入操作之前，将文件指针定位到文件结尾。 |
| \_O\_RDONLY  | 打开文件以供只读。 |
| \_O\_TEXT  | 在文本（转换）模式下打开文件。 |
| \_O\_WTEXT  | 在 Unicode（转换 UTF-16）模式下打开文件。 |

_open_osfhandle  调用将 Win32 文件句柄的所有权转移给文件描述符。 要使用- _open_osfhandle  关闭已打开的文件，请调用 [\_close](close.md)。 底层 OS 文件句柄也由对 _close 的调用关闭  。 请勿对原始句柄调用 Win32 函数 CloseHandle  。 如果文件描述符归**文件&#42;** 流，然后调用[fclose](fclose-fcloseall.md)关闭文件描述符和基础句柄。 在此情况下，请勿在文件描述符上调用 _close，或在原始句柄上调用 CloseHandle   。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
