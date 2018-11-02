---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: de2aa99375f588d682b714632590ba8e0db8ddcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597218"
---
# <a name="stacksize"></a>STACKSIZE

设置堆栈的大小（以字节为单位）。

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>备注

设置堆栈的等效方法是使用[堆栈分配](../../build/reference/stack-stack-allocations.md)(/stack) 选项。 了解有关该选项的详细信息的文档*保留*和`commit`参数。

此选项对 Dll 无效。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)