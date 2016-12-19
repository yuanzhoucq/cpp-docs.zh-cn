---
title: "编译器错误 C3804 | Microsoft Docs"
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
  - "C3804"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3804"
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3804
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“property\_accessor”: 属性的访问器方法必须全部是静态或全部是非静态的  
  
 当定义不常用属性时，访问器函数既可以是静态的也可以是实例，但不能两者都是。  
  
 有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3804。  
  
```  
// C3804.cpp  
// compile with: /c /clr  
ref struct A {  
  
   property int i {  
      static int get() {}  
      void set(int i) {}  
   }   // C3804 error  
  
   // OK  
   property int j {  
      int get() { return 0; }  
      void set(int i) {}  
   }  
  
   property int k {  
      static int get() { return 0; }  
      static void set(int i) {}  
   }  
};  
```