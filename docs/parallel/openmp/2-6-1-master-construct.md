---
title: "2.6.1 master Construct | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.1 master Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**母版** 指令标识指定构造块该团队的主线程执行的构造。  **母版** 指令的语法如下所示:  
  
```  
#pragma omp master new-line  
   structured-block  
```  
  
 在团队中的其他线程不执行关联的构造块。  没有提示的关卡在项到或从主构造退出。