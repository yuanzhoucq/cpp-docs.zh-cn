---
title: "编译器错误 C3904 | Microsoft Docs"
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
  - "C3904"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3904"
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3904
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“property\_accessor”: 必须指定 number 参数  
  
 对照属性维数，检查 `get` 和 `set` 方法中参数的个数。  
  
-   `get` 方法的参数个数必须等于属性的维数，或者为零（对于非索引属性）。  
  
-   `set` 方法的参数个数必须比属性的维数多一个。  
  
 有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3904。  
  
```  
// C3904.cpp  
// compile with: /clr /c  
ref class X {  
   property int P {  
      // set  
      void set();   // C3904  
      // try the following line instead  
      // void set(int);  
  
      // get  
      int get(int, int);   // C3904  
      // try the following line instead  
      // int get();  
   };  
};  
```  
  
## 示例  
 下面的示例生成 C3904。  
  
```  
// C3904b.cpp  
// compile with: /clr /c  
ref struct X {  
   property int Q[double, double, float, float, void*, int] {  
      // set  
      void set(double, void*);   // C3904  
      // try the following line instead  
      // void set(double, double, float, float, void*, int, int);  
  
      // get  
      int get();   // C3904  
      // try the following line instead  
      // int get(double, double, float, float, void*, int);  
   }  
};  
```