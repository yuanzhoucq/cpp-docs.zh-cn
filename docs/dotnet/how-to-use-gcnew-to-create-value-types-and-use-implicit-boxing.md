---
title: "如何：使用 gcnew 创建值类型并使用隐式装箱 | Microsoft Docs"
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
  - "装箱, implicit"
  - "gcnew 关键字 [C++], 创建值类型"
  - "值类型, 创建"
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 如何：使用 gcnew 创建值类型并使用隐式装箱
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用值类型上的 [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) 将创建装箱值类型，主机上就放置，垃圾回收堆中。  
  
## 示例  
  
```  
// vcmcppv2_explicit_boxing4.cpp  
// compile with: /clr  
public value class V {  
public:  
   int m_i;  
   V(int i) : m_i(i) {}  
};  
  
public ref struct TC {  
   void do_test(V^ v) {  
      if (v != nullptr)  
         ;  
      else  
         ;  
   }  
};  
  
int main() {  
   V^ v = gcnew V(42);  
   TC^ tc = gcnew TC;  
   tc->do_test(v);  
}  
```  
  
## 请参阅  
 [装箱](../windows/boxing-cpp-component-extensions.md)