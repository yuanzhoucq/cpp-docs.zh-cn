---
title: 2.4 工作共享构造 |Microsoft 文档
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
ms.openlocfilehash: c00eb94055f26954a283a6172f69228804832ac4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689631"
---
# <a name="24-work-sharing-constructs"></a>2.4 工作共享构造
工作共享构造分布在遇到此警告的团队成员之间的关联语句的执行。 工作共享指令不启动新线程，并且在进入工作共享构造没有不存在任何隐含的障碍。  
  
 序列的工作共享构造和**屏障**遇到指令必须是相同的组中的每个线程。  
  
 OpenMP 定义下列工作共享构造，并描述了这些内容在以下各节：  
  
-   **有关**指令  
  
-   **部分**指令  
  
-   **单个**指令