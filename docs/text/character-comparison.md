---
title: 字符比较
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 075a22634f254c2ea634a1171ee157971fe5918e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410689"
---
# <a name="character-comparison"></a>字符比较

使用以下提示：

- 比较已知的前导字节的 ASCII 字符正常工作：

    ```cpp
    if( *sz1 == 'A' )
    ```

- 比较两个未知的字符需要使用一个 Mbstring.h 中定义的宏：

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   这可确保这两个字节的双字节字符会比较相等性。

## <a name="see-also"></a>请参阅

[MBCS 编程提示](../text/mbcs-programming-tips.md)<br/>
[缓冲区溢出](../text/buffer-overflow.md)
