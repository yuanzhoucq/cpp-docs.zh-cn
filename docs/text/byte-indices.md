---
title: 字节索引
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 4e19868e5297e1c1615efabde2aee418bc53c51e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448810"
---
# <a name="byte-indices"></a>字节索引

使用以下提示：

- 使用转换为字符串的字节索引带来了问题类似于所引起的指针操作。 请考虑此扫描字符串以反斜杠字符的示例：

    ```cpp
    while ( rgch[ i ] != '\\' )
        i++;
    ```

   这可能会编制索引结尾字节，前导字节，并因此它可能不指向`character`。

- 使用[_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)函数来解决上述问题：

    ```cpp
    while ( rgch[ i ] != '\\' )
        i += _mbclen ( rgch + i );
    ```

   它正确地索引前导字节，因此到`character`。 `_mbclen`函数确定字符 （1 或 2 个字节） 的大小。

## <a name="see-also"></a>请参阅

[MBCS 编程提示](../text/mbcs-programming-tips.md)<br/>
[字符串中的最后一个字符](../text/last-character-in-a-string.md)