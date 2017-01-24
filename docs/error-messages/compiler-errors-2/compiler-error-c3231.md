---
title: "编译器错误 C3231 | Microsoft Docs"
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
  - "C3231"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3231"
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3231
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“arg”: 模板类型参数不能使用泛型类型参数  
  
 模板在编译时实例化，而泛型在运行时实例化。  因此，不可能生成可调用模板的泛型代码，因为当泛型类型最终已知时，模板不能在运行时进行实例化。  
  
 下面的示例生成 C3231：  
  
```  
// C3231.cpp  
// compile with: /clr /LD  
template <class T> class A;  
  
generic <class T>  
ref class C {  
   void f() {  
      A<T> a;   // C3231  
   }  
};  
```