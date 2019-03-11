---
title: 字符串中的最后一个字符
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 4c99628cd12738fabb877a94cfd04a4033ee45aa
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740284"
---
# <a name="last-character-in-a-string"></a>字符串中的最后一个字符

使用以下提示：

- 尾字节范围重叠在许多情况下设置的 ASCII 字符。 可安全地用于按字节扫描任何控制字符 (小于 32)。

- 请考虑以下可能会检查以查看是否在字符串中的最后一个字符是反斜杠字符的代码行：

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   因为`strlen`不是 MBCS 感知型，它将返回的字节，不是数字的字符，数中的多字节字符串。 另请注意，在某些代码页 (932，例如)，'\\(0x5c) 是一个有效的结尾字节 (`sz`是一个 C 字符串)。

   一个可能的解决方案是重写此方法的代码：

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   此代码使用 MBCS 函数`_mbsrchr`和`_mbsinc`。 由于这些函数是 mbcs，它们可以区分 '\\字符和结尾字节\\。 如果在字符串中的最后一个字符为 null (\0)，代码将执行一些操作。

## <a name="see-also"></a>请参阅

[MBCS 编程提示](../text/mbcs-programming-tips.md)<br/>
[字符赋值](../text/character-assignment.md)
