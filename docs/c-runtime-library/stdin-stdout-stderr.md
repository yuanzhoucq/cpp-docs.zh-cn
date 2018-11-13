---
title: stdin、stdout、stderr
ms.date: 10/23/2018
f1_keywords:
- stdin
- stderr
- stdout
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
ms.openlocfilehash: f9ed1f842bd174c2b926572856152cd69ade5a56
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328014"
---
# <a name="stdin-stdout-stderr"></a>stdin、stdout、stderr

## <a name="syntax"></a>语法

```
FILE *stdin;
FILE *stdout;
FILE *stderr;
#include <stdio.h>
```

## <a name="remarks"></a>备注

以下是输入、输出和错误输出的标准流。

默认情况下，标准输入是从键盘读取的，而标准输出和错误输出将打印到屏幕。

下列流指针可用于访问标准流：

|指针|流|
|-------------|------------|
|`stdin`|标准输入|
|`stdout`|标准输出|
|`stderr`|标准错误|

这些指针可用作函数自变量。 某些函数（如 [getchar](../c-runtime-library/reference/getchar-getwchar.md) 和 [putchar](../c-runtime-library/reference/putchar-putwchar.md)）会自动使用 `stdin` 和 `stdout`。

这些指针是常量，无法分配新的值。 [freopen](../c-runtime-library/reference/freopen-wfreopen.md) 函数可用于将流重定向到磁盘文件或其他设备。 操作系统使您可以在命令级别重定向程序的标准输入和输出。

## <a name="see-also"></a>请参阅

[流 I/O](../c-runtime-library/stream-i-o.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)
