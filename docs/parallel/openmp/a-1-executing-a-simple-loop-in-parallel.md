---
title: A.1 并行执行简单的循环 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b2fbac6ce31d2dbc56a4ef6d9fe87c14d5ee16
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686121"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   并行执行简单循环
下面的示例演示如何并行执行简单的循环使用`parallel for`指令 ([部分 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md)第 16 页上)。 循环迭代变量是默认情况下，为私有的因此不需要专用子句中显式指定。  
  
```  
#pragma omp parallel for  
    for (i=1; i<n; i++)  
        b[i] = (a[i] + a[i-1]) / 2.0;  
```