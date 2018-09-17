---
title: STACKSIZE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9b61febedde1a2647df6312a8588b08c6bdad7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705557"
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