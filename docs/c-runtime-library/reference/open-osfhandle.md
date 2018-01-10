---
title: "_open_osfhandle | Microsoft 文档"
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _open_osfhandle
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
dev_langs: C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff05c99180ff8933316e1db9366da3b985c10305
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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

*osfhandle*  
操作系统文件句柄。

*flags*  
允许的操作类型。

## <a name="return-value"></a>返回值

如果成功，`_open_osfhandle` 返回 C 运行时文件描述符。 否则，它将返回-1。

## <a name="remarks"></a>备注

`_open_osfhandle`函数分配的 C 运行时文件描述符，并将其与指定的操作系统文件句柄关联*osfhandle*。 *标志*自变量是由一个或多个 Fcntl.h 中定义的清单常量构成一个整数表达式。 当两个或多个清单常量来形成*标志*自变量，这些常量将与按位 OR 运算符合并 ( **&#124;** )。

Fcntl.h 中定义的以下清单常量：

**\_O\_追加**  
在执行每个写入操作之前，将文件指针定位到文件结尾。

**\_O\_RDONLY**  
打开文件以供只读。

**\_O\_文本**  
在文本（转换）模式下打开文件。

**\_O\_WTEXT**  
在 Unicode（转换 UTF-16）模式下打开文件。

要关闭使用打开的文件`_open_osfhandle`，调用[\_关闭](../../c-runtime-library/reference/close.md)。 通过调用也关闭基础的操作系统文件句柄`_close`，因此不需要调用 Win32 函数`CloseHandle`对原始句柄。 如果由所拥有的文件描述符`FILE *`流，然后调用[fclose](../../c-runtime-library/reference/fclose-fcloseall.md)上`FILE *`文件描述符和基础句柄，也会关闭流。 在这种情况下，不要调用`_close`上的文件描述符。

## <a name="requirements"></a>惠?

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`_open_osfhandle`|\<io.h>|

有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)  
