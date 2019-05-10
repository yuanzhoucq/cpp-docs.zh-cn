---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 2d27b4fd596098f4abc5bb0d804d87bd08f70a60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318350"
---
# <a name="stacksize"></a>STACKSIZE

设置堆栈的大小（以字节为单位）。

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>备注

设置堆栈的等效方法是使用[堆栈分配](stack-stack-allocations.md)(/stack) 选项。 了解有关该选项的详细信息的文档*保留*和`commit`参数。

此选项对 Dll 无效。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](rules-for-module-definition-statements.md)
