---
title: 2.4.3 单一构造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81abf5324c215b9011ecbd774626a213c2eda653
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376494"
---
# <a name="243-single-construct"></a>2.4.3 single 构造

**单个**指令标识一个构造，它指定由团队 （不一定是主线程） 中只有一个线程执行相关联的结构化的块。 语法**单个**指令是按如下所示：

```
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

子句是以下值之一：

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**copyprivate (** *变量列表* **)**

**nowait**

没有后的隐式屏障**单个**构造，除非**nowait**指定子句。

限制**单个**指令如下所示：

- 只有一个**nowait**子句可出现在**单个**指令。

- **Copyprivate**子句必须不能用于**nowait**子句。

## <a name="cross-references"></a>交叉引用：

- **私有**， **firstprivate**，和**copyprivate**子句，请参阅[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。