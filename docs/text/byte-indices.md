---
title: 字节索引
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 5305a977c23d7a978a89c84809cc6fab8c5731eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410715"
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
