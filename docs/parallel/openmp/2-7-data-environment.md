---
title: 2.7 数据环境 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1b0f253ce14ffc5d3740e582a9a51feea56ad32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690060"
---
# <a name="27-data-environment"></a>2.7 数据环境
本节介绍指令和多个子句，用于控制数据环境并行区域，在执行期间，如下所示：  
  
-   A **threadprivate**指令 （请参阅以下部分） 提供可以使文件范围、 命名空间范围或静态的块范围变量为线程本地。  
  
-   可在指令以并行或工作共享构造的持续时间内控制变量的共享属性中指定的子句中所述[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。