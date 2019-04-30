---
title: 递增和递减指针
ms.date: 11/04/2016
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
ms.openlocfilehash: cdaee3d13a8ceab47f62100953a0eb6e51bfc255
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410650"
---
# <a name="incrementing-and-decrementing-pointers"></a>递增和递减指针

使用以下提示：

- 指向前导字节而非尾字节。 它是有一个指针指向结尾字节通常不安全的。 它是转发而不是按相反的顺序扫描一个字符串，通常更安全。

- 有指针递增/递减函数和宏可在整个字符上移动：

    ```cpp
    sz1++;
    ```

   将成为：

    ```cpp
    sz1 = _mbsinc( sz1 );
    ```

   `_mbsinc`并`_mbsdec`函数正确递增和递减中`character`单位，与字符大小无关。

- 对于递减，你需要指向的字符串，如以下所示：

    ```cpp
    sz2--;
    ```

   将成为：

    ```cpp
    sz2 = _mbsdec( sz2Head, sz2 );
    ```

   或者，头指针可以指向有效的字符在字符串中，以便：

    ```cpp
    sz2Head < sz2
    ```

   必须具有指向已知的有效前导字节的指针。

- 你可能想要维护一个指向上一个字符的更快地调用`_mbsdec`。

## <a name="see-also"></a>请参阅

[MBCS 编程提示](../text/mbcs-programming-tips.md)<br/>
[字节索引](../text/byte-indices.md)
