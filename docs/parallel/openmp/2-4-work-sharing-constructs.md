---
title: 2.4 工作共享构造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719b33698b708761f0cd56e65a70a6ea8fa3b053
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411113"
---
# <a name="24-work-sharing-constructs"></a>2.4 工作共享构造

工作共享构造分布情况下遇到此团队的成员相关联的语句的执行。 工作共享指令不启动新线程，并且在进入工作共享构造没有不存在任何隐式的障碍。

一系列工作共享构造并**屏障**遇到指令必须为团队中每个线程相同。

OpenMP 定义以下工作共享构造和以下各节中描述了这些：

- **有关**指令

- **部分**指令

- **单个**指令