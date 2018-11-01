---
title: 2.4 工作共享构造
ms.date: 11/04/2016
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
ms.openlocfilehash: e7bf8d37ecdc6a3ef451c9d9746fb47a76a16eb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502877"
---
# <a name="24-work-sharing-constructs"></a>2.4 工作共享构造

工作共享构造分布情况下遇到此团队的成员相关联的语句的执行。 工作共享指令不启动新线程，并且在进入工作共享构造没有不存在任何隐式的障碍。

一系列工作共享构造并**屏障**遇到指令必须为团队中每个线程相同。

OpenMP 定义以下工作共享构造和以下各节中描述了这些：

- **有关**指令

- **部分**指令

- **单个**指令