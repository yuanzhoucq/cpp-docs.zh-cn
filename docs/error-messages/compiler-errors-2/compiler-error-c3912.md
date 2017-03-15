---
title: "编译器错误 C3912 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3912"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3912"
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3912
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“event”: 事件的类型必须是委托类型  
  
 声明了事件，但它的类型不正确。  
  
 有关更多信息，请参见[事件](../../windows/event-cpp-component-extensions.md)。  
  
 下面的示例生成 C3912：  
  
```  
// C3912.cpp  
// compile with: /clr  
delegate void H();  
ref class X {  
   event int Ev;   // C3912  
   event H^ Ev2;   // OK  
};  
```