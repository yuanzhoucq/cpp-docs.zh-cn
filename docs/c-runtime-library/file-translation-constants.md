---
title: 文件翻译常量
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
ms.openlocfilehash: ed2fae935850837ebace880d78c206754b3061bd
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375913"
---
# <a name="file-translation-constants"></a>文件翻译常量

## <a name="syntax"></a>语法

```
#include <stdio.h>
```

## <a name="remarks"></a>备注

这些常数指定转换模式（“b”  或“t”  ）。 模式包含在指定访问类型（“r”  “w”  、“a”  、“r+”  、“w+”  、“a+”  ）的字符串中。

转换模式如下所示：

- **t**

   在文本（已转换）模式下打开。 在这种模式下，输入时，回车换行 (CR-LF) 组合将转换为单一的换行 (LF)；输出时，LF 字符将转换为 CR-LF 组合。 CTRL+Z 也将在输入时解释为文件尾字符。 在打开以进行读取或读取和写入的文件中，`fopen` 将检查文件末尾的 Ctrl+Z 并在可能的情况下将其移除。 这样做是因为，使用 `fseek` 和 `ftell` 函数在以 Ctrl+Z 结尾的文件中移动时，可能导致 `fseek` 在文件末尾附近错误操作。

   > [!NOTE]
   > “t”  选项不是 `fopen` 和 `freopen` 的 ANSI 标准的一部分。 它是一个 Microsoft 扩展，不应在需要 ANSI 可移植性的地方使用。

- **b**

   在二进制（未转换）模式下打开。 禁止上述的转换。

如果在 mode  中未给出 t  或 b  ，则转换模式由默认模式变量 [_fmode](../c-runtime-library/fmode.md) 定义。 有关使用文本和二进制模式的详细信息，请参阅[文本和二进制模式文件 I/O](../c-runtime-library/text-and-binary-mode-file-i-o.md)。

## <a name="see-also"></a>请参阅

[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen、_wfopen_wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)
