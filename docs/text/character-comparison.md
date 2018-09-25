---
title: 字符比较 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3412939bac9dace6f3abaacda75ed73d6e60f21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428065"
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