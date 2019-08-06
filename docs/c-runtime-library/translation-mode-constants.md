---
title: 翻译模式常量
ms.date: 11/04/2016
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
ms.openlocfilehash: a86c0c1a0b70613c6e7749c78f58f6dfb3602d4d
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376277"
---
# <a name="translation-mode-constants"></a>翻译模式常量

## <a name="syntax"></a>语法

```
#include <fcntl.h>
```

## <a name="remarks"></a>备注

`_O_BINARY` 和 `_O_TEXT` 清单常数将决定文件（`_open` 和 `_sopen`）的转换模式或流 (`_setmode`) 的转换模式。

允许的值包括：

|||
|-|-|
`_O_TEXT`  | 在文本（已转换）模式下打开文件。 输入时回车符–换行符 (CR-LF) 组合将转换为单个换行符 (LF)。 输出时换行符将转换为 CR-LF 组合。 CTRL+Z 也将在输入时解释为文件尾字符。 在打开以进行读取或读取和写入的文件中，`fopen` 将检查文件末尾的 Ctrl+Z 并在可能的情况下将其移除。 这样做是因为，使用 `fseek` 和 `ftell` 函数在以 Ctrl+Z 结尾的文件中移动时，可能导致 `fseek` 在文件末尾附近错误操作。
`_O_BINARY`  | 在二进制（未转换）模式下打开文件。 禁止上述的转换。
`_O_RAW`  | 与 `_O_BINARY` 相同。 支持 C 2.0 兼容性。

有关详细信息，请参阅[文本和二进制模式文件 I/O](../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文件转换](../c-runtime-library/file-translation-constants.md)。

## <a name="see-also"></a>请参阅

[_open、_wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)
