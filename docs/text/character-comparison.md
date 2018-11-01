---
title: 字符比较
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 206910d4b76f93a92ee5230a227d6f0346a85e61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615403"
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