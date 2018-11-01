---
title: _open_osfhandle
ms.date: 05/29/2018
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
ms.openlocfilehash: e8b7dc097c1af60894c627b8b660c4d9d81361db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519452"
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

如果成功， **_open_osfhandle**返回 C 运行时文件描述符。 否则，则返回-1。

## <a name="remarks"></a>备注

**_Open_osfhandle**函数分配 C 运行时文件描述符，并将它与由指定的操作系统文件句柄相关联*osfhandle*。 若要避免编译器警告，强制转换*osfhandle*从参数**处理**到**intptr_t**。 *标志*参数是一个整数表达式从一个或多个清单常量中定义\<fcntl.h >。 当两个或多个清单常量来形成*标志*自变量，这些常量将与按位 OR 运算符合并 ( **&#124;** )。

这些常量在清单中定义\<fcntl.h >:

|||
|-|-|
**\_O\_追加**|在执行每个写入操作之前，将文件指针定位到文件结尾。
**\_O\_RDONLY**|打开文件以供只读。
**\_O\_TEXT**|在文本（转换）模式下打开文件。
**\_O\_WTEXT**|在 Unicode（转换 UTF-16）模式下打开文件。

**_Open_osfhandle**调用将 Win32 文件句柄的所有权转移到的文件描述符。 若要关闭与打开的文件 **_open_osfhandle**，调用[\_关闭](close.md)。 通过调用也关闭基础 OS 文件句柄 **_close**，因此不需要调用 Win32 函数**CloseHandle**对原始句柄。 如果文件描述符归**文件&#42;** 流，然后调用[fclose](fclose-fcloseall.md)上的**文件&#42;** 流也会关闭这两个文件描述符和基础句柄。 在这种情况下，不要调用 **_close**上的文件描述符。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
