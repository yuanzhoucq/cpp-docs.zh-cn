---
title: "编译器错误 C3728 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3728"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3728"
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3728
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“event”: 事件没有引发方法  
  
 对于不允许从事件在其中定义的类之外引发事件的语言（如 C\#），通过 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指令包括了使用该语言创建的元数据；使用 CLR 编程的 Visual C\+\+ 程序尝试引发该事件。  
  
 若要在使用 C\# 之类的语言开发的程序中引发事件，则包含该事件的类还需要定义引发该事件的公共方法。