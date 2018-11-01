---
title: 2.7.2.7 copyin
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 65bb8faba085e5582e779fa0e9d5bf1a91a39f0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545439"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin

**Copyin**子句提供了一种机制来将分配到相同的值**threadprivate**团队执行并行区域中的每个线程的变量。 对于每个变量中指定**copyin**复制子句，团队在主线程中变量的值，像是通过分配到并行区域的开始处的线程专用副本。 语法**copyin**子句如下所示：

```

copyin(
variable-list
)

```

对限制**copyin**子句如下所示：

- 中指定的变量**copyin**子句必须具有可访问的、 明确的复制赋值运算符。

- 中指定的变量**copyin**子句必须**threadprivate**变量。