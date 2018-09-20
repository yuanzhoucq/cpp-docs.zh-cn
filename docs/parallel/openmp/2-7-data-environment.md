---
title: 2.7 数据环境 |Microsoft Docs
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
ms.openlocfilehash: 17c60c621defa15c034f57d0af8f14637db54f03
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378132"
---
# <a name="27-data-environment"></a>2.7 数据环境

本节介绍指令和多个子句，用于控制数据环境的并行区域，在执行期间，如下所示：

- 一个**threadprivate**指令 （请参阅以下部分） 提供了可使文件范围、 命名空间范围或静态的块范围变量为线程本地。

- 要并行或工作共享构造的持续时间内控制变量的共享属性的指令只能指定子句中所述[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。