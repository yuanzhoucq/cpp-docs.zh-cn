---
title: "编译器错误 C3908 | Microsoft Docs"
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
  - "C3908"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3908"
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3908
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

访问级别的限制低于“construct”的限制  
  
 属性访问器方法（get 或 set）的访问限制不能低于在属性自身上指定的访问限制。对于事件访问器方法，与此类似。  
  
 有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)和[事件](../../windows/event-cpp-component-extensions.md)。  
  
 下面的示例生成 C3908：  
  
```  
// C3908.cpp  
// compile with: /clr  
ref class X {  
protected:  
   property int i {  
   public:   // C3908 property i is protected   
      int get();  
   private:  
      void set(int);   // OK more restrictive  
   };  
};  
```