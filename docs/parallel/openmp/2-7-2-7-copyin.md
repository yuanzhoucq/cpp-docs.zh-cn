---
title: 2.7.2.7 copyin
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 20db32530ee60967245497cdfb12a0fce103f7b7
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519524"
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