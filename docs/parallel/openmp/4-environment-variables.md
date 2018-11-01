---
title: 4. 环境变量
ms.date: 11/04/2016
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 0dec302762ad22fc3c7f6691ef63df1b07d5940d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456597"
---
# <a name="4-environment-variables"></a>4.环境变量

本章节介绍了 OpenMP C 和 c + + API 环境变量 （或等效的特定于平台的机制），以控制并行代码的执行。  环境变量的名称必须为大写。 分配给它们的值是不区分大小写，并可能有前导和尾随空格。  程序启动后的值对的修改将被忽略。

环境变量如下所示：

- **OMP_SCHEDULE**设置运行时计划类型和块区大小。

- **OMP_NUM_THREADS**设置要在执行期间使用的线程数。

- **OMP_DYNAMIC**启用或禁用动态调整线程数。

- **OMP_NESTED**启用或禁用嵌套并行度。

这一章中的示例仅演示如何可能在 Unix C shell (csh) 环境中设置这些变量。 在 Korn shell 和 DOS 环境操作类似，如下所示：

csh: setenv OMP_SCHEDULE"动态"

ksh： 导出 OMP_SCHEDULE ="动态"

DOS： 设置 OMP_SCHEDULE ="动态"