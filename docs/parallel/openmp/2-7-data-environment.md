---
title: "2.7 数据环境 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e018a2c1b20bef640852ced913dc90266e733c06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="27-data-environment"></a>2.7 数据环境
本节介绍指令和多个子句，用于控制数据环境并行区域，在执行期间，如下所示：  
  
-   A **threadprivate**指令 （请参阅以下部分） 提供可以使文件范围、 命名空间范围或静态的块范围变量为线程本地。  
  
-   可在指令以并行或工作共享构造的持续时间内控制变量的共享属性中指定的子句中所述[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。