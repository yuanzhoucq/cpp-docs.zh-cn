---
title: "描述块 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "块, 描述"
  - "描述块"
  - "NMAKE 程序, 描述块"
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 描述块
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述块是后面可跟有命令块的依赖项行：  
  
```  
targets... : dependents...  
    commands...  
```  
  
 依赖项行指定一或多个目标以及零或多个依赖项。  目标必须位于行首。  用冒号 \(:\) 将目标和依赖项分开；允许使用空格或制表符。  若要拆分行，请在目标或依赖项后面使用反斜杠 \(\\ \)。  如果目标不存在、目标的时间戳比依赖项早或者目标是[伪目标](../build/pseudotargets.md)，则 NMAKE 执行命令。  如果某依赖项是其他地方的目标，并且不存在或对于自己的依赖项已过期，则 NMAKE 在更新当前依赖项之前更新该依赖项。  
  
## 您想进一步了解什么？  
 [目标](../build/targets.md)  
  
 [依赖项](../build/dependents.md)  
  
## 请参阅  
 [NMAKE 参考](../build/nmake-reference.md)