---
title: "编译器错误 C3765 | Microsoft Docs"
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
  - "C3765"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3765"
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3765
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“event”: 在标记为 event\_receiver 的类\/结构“type”中不能定义事件  
  
 如果使用 [event\_receiver](../../windows/event-receiver.md) 特性标记某类，则该类不能包含 [\_\_event](../../cpp/event.md) 声明。  
  
 下面的示例生成 C3765：  
  
```  
// C3765.cpp  
[event_receiver(native)]  
struct ER2 {  
   __event void f();   // C3765  
   __event void b(int);   // C3765  
};  
```