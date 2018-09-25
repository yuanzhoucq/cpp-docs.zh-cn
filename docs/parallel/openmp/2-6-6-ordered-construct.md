---
title: 2.6.6 ordered 构造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b83c3dfc13b231a1314343a1dff496acf7a99b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412192"
---
# <a name="266-ordered-construct"></a>2.6.6 ordered 构造

结构化的块以下**排序**迭代会执行顺序循环中的顺序执行指令。 语法**排序**指令是按如下所示：

```
#pragma omp ordered new-linestructured-block
```

**排序**指令必须是动态的范围内**有关**或**并行的**构造。 **有关**或**为并行**指令所属**排序**构造绑定必须具有**排序**子句指定中所述[部分 2.4.1](../../parallel/openmp/2-4-1-for-construct.md)第 11 页上。 执行过程中的**有关**或**的并行**通过构造**排序**子句，**排序**严格中执行构造将顺序执行循环中执行顺序。

限制**排序**指令如下所示：

- 使用循环的迭代**有关**构造必须不超过一次，执行相同的有序的指令，同时必须执行多个**排序**指令。