---
title: "initonly (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "initonly_cpp"
  - "initonly"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "initonly 特性 [C++]"
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# initonly (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**initonly** 是一个区分上下文关键字变量赋值可以只在作为声明的一部分或在同一类的静态构造函数。  
  
 下面的示例演示如何使用 `initionly`：  
  
```  
// mcpp_initonly.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   initonly  
   static int staticConst1;  
  
   initonly  
   static int staticConst2 = 0;  
  
   static Y1() {  
      staticConst1 = 0;  
   }  
};  
```  
  
## 请参阅  
 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)