---
title: "如何：显式请求装箱 | Microsoft Docs"
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
  - "装箱, 显式请求"
ms.assetid: 1359e6e5-162d-4f5d-9b6a-1690d93df3ee
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何：显式请求装箱
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过分配变量显式请求装箱给 `Object`类型的变量。  
  
## 示例  
  
```  
// vcmcppv2_explicit_boxing3.cpp  
// compile with: /clr  
using namespace System;  
  
void f(int i) {  
   Console::WriteLine("f(int i)");  
}  
  
void f(Object ^o) {  
   Console::WriteLine("f(Object^ o)");  
}  
  
int main() {  
   int i = 5;  
   Object ^ O = i;   // forces i to be boxed  
   f(i);  
   f(O);  
   f( (Object^)i );  // boxes i  
}  
```  
  
  **f\(int i\)**  
**f \(Object^ o\)**  
**f \(Object^ o\)**   
## 请参阅  
 [装箱](../windows/boxing-cpp-component-extensions.md)