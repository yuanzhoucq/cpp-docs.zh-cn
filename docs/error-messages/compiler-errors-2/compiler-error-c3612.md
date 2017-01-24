---
title: "编译器错误 C3612 | Microsoft Docs"
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
  - "C3612"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3612"
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3612
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 密封类不能是抽象的  
  
 默认情况下使用 `value`（或 [\_\_value](../../misc/value.md)）定义的类型为密封类型，并且类在实现其基类的所有方法之前为抽象类。  密封的抽象类既不可以是基类，也不可被实例化。  
  
 有关详细信息，请参阅[类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下面的示例生成 C3612：  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```