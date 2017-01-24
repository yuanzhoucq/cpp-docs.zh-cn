---
title: "多个描述块中的目标 | Microsoft Docs"
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
helpviewer_keywords: 
  - "块, 多重描述"
  - "描述块"
  - "多重描述块"
ms.assetid: 8618dcd9-c11d-4562-91a7-0c904ed438a8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多个描述块中的目标
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用不同的命令更新多个描述块中的目标，请在目标与依赖项之间指定两个连续的冒号 \(::\)。  
  
```  
target.lib :: one.asm two.asm three.asm  
    ml one.asm two.asm three.asm  
    lib target one.obj two.obj three.obj  
target.lib :: four.c five.c  
    cl /c four.c five.c  
    lib target four.obj five.obj  
```  
  
## 请参阅  
 [目标](../build/targets.md)