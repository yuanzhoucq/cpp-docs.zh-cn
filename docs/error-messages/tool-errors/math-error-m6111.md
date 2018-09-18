---
title: 数学错误 M6111 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a55ec6b7cdf0b6e4c15bd283dde77c610698fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074820"
---
# <a name="math-error-m6111"></a>数学错误 M6111

堆栈下溢

浮点运算导致堆栈下溢 8087/287/387 协处理器或仿真程序上。

此错误通常通过调用引起`long double`不返回值的函数。 例如，以下生成此错误在编译和运行：

```
long double ld() {};
main ()
{
  ld();
}
```

程序终止，退出代码为 139。