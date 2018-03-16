---
title: "2.4 工作共享构造 |Microsoft 文档"
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
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 476e4e23b22527accaa095d80b827c95aed58c15
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2018
---
# <a name="24-work-sharing-constructs"></a>2.4 工作共享构造
工作共享构造分布在遇到此警告的团队成员之间的关联语句的执行。 工作共享指令不启动新线程，并且在进入工作共享构造没有不存在任何隐含的障碍。  
  
 序列的工作共享构造和**屏障**遇到指令必须是相同的组中的每个线程。  
  
 OpenMP 定义下列工作共享构造，并描述了这些内容在以下各节：  
  
-   **for** directive  
  
-   **部分**指令  
  
-   **单个**指令