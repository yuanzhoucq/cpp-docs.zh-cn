---
title: 2.7 数据环境
ms.date: 11/04/2016
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
ms.openlocfilehash: b65dfc7d7694b36ef4f89351579cd73e07ab537c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491958"
---
# <a name="27-data-environment"></a>2.7 数据环境

本节介绍指令和多个子句，用于控制数据环境的并行区域，在执行期间，如下所示：

- 一个**threadprivate**指令 （请参阅以下部分） 提供了可使文件范围、 命名空间范围或静态的块范围变量为线程本地。

- 要并行或工作共享构造的持续时间内控制变量的共享属性的指令只能指定子句中所述[部分 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。