---
title: 2.7.2.2 firstprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3e6ad966f4cf895da9374798f6c9a4079ccc2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400960"
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

**Firstprivate**子句提供的提供的功能超集**专用**子句。 语法**firstprivate**子句如下所示：

```
firstprivate(variable-list)
```

中指定的变量*变量列表*有**专用**子句语义，如中所述[部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上。 初始化或构造会发生像它每个线程，在构造的线程的执行前一次执行情况。 有关**firstprivate**并行构造的子句，新的私有对象的初始值是立即在遇到它的线程的并行构造之前存在的原始对象的值。 有关**firstprivate**工作共享构造的子句，每个线程都执行的工作共享构造的新私有对象的初始值是原始的时间点之前存在的对象的值，在同一线程遇到工作共享构造。 此外，对于 c + + 对象，每个线程的新私有对象是从原始对象构造的副本。

对限制**firstprivate**子句如下所示：

- 中指定的变量**firstprivate**子句不能是不完整类型或引用类型。

- 指定为类类型的变量**firstprivate**必须具有可访问的、 明确的复制构造函数。

- 专用并行区域内或在中都出现的变量**减少**子句**并行**不能在指定指令**firstprivate**上的子句绑定到并行构造的工作共享指令。