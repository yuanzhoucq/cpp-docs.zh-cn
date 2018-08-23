---
title: 2.8 指令绑定 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02492b228b4bb47a800955f078a59ce680312a87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689449"
---
# <a name="28-directive-binding"></a>2.8 指令绑定
动态绑定的指令必须遵守以下规则：  
  
-   **为**，**部分**，**单个**， **master**，和**屏障**指令将绑定到动态封闭**并行**，如果存在，而不考虑任何值**如果**可能出现该指令上的子句。 如果当前正在执行任何并行区域，团队组成只有主线程被不执行指令。  
  
-   **排序**指令将绑定到动态封闭**为**。  
  
-   **原子**指令强制实施与的独占访问权**原子**中的所有线程，而不仅仅是当前的团队中的指令。  
  
-   **关键**指令强制实施与的独占访问权**关键**中的所有线程，而不仅仅是当前的团队中的指令。  
  
-   指令可以永远不会将绑定到任何外部的最近指令动态封闭**并行**。