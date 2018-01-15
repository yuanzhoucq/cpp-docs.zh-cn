---
title: "A.1 并行执行简单的循环 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b8e425363b81954a72d0eb08491c384c47c695d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   并行执行简单循环
下面的示例演示如何并行执行简单的循环使用`parallel for`指令 ([部分 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md)第 16 页上)。 循环迭代变量是默认情况下，为私有的因此不需要专用子句中显式指定。  
  
```  
#pragma omp parallel for  
    for (i=1; i<n; i++)  
        b[i] = (a[i] + a[i-1]) / 2.0;  
```