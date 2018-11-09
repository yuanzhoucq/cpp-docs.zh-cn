---
title: 文件读-写访问常量
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
ms.openlocfilehash: 7bf16271c0d58e3d87e4c24795ec0bd1ee1ccb89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666163"
---
# <a name="file-readwrite-access-constants"></a>文件读取/写入访问常量

## <a name="syntax"></a>语法

```
#include <stdio.h>
```

## <a name="remarks"></a>备注

这些常量指定为文件请求的访问类型（“a”、“r”或“w”）。 可以使用访问类型来指定[转换模式](../c-runtime-library/file-translation-constants.md)（“b”或“t”）和 [ 模式](../c-runtime-library/commit-to-disk-constants.md)（“c”或“n”）。

访问类型如下表中所述：

|访问类型|描述|
|----------|----------------|
|**“r”**|打开以便读取。 如果文件不存在或找不到，调用以打开文件操作将失败。|
|**“w”**|打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。|
|**“a”**|打开以便在文件末尾进行写入（追加）；如果文件不存在，则首先创建它。 所有写入操作均在文件末尾发生。 虽然使用 `fseek` 或 `rewind` 可重新定位文件指针，但在执行任何写入操作前，文件指针将始终被移回文件末尾。 |
|**“r+”**|打开以便读取和写入。 如果文件不存在或找不到，调用以打开文件操作将失败。|
|**“w+”**|打开用于读取和写入的空文件。 如果给定文件存在，则其内容会被销毁。|
|**“a+”**|与“a+”相同，但还允许读取。|

指定“r+”、“w+”或“a+”类型时，允许读取和写入（文件将处于打开状态以进行“更新”）。 但是，在读取与写入之间切换时，必须有中间 `fflush`、`fsetpos`、`fseek` 或 `rewind` 操作。 可以为 `fsetpos` 或 `fseek` 操作指定当前位置。

## <a name="see-also"></a>请参阅

[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen、_wfopen_wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen、_wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)