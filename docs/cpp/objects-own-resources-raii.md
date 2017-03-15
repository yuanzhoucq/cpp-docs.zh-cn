---
title: "对象所有资源 (RAII) | Microsoft Docs"
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
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# 对象所有资源 (RAII)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

记住对象的资源。  也称此原则是“"获取资源即初始化" \(RAII\) RAII”或“”。  
  
## 示例  
 将各“新”对象，因为构造函数参数传递给拥有它的其他命名对象 \(通常 unique\_ptr\)。  
  
```cpp  
void f() {  
  unique_ptr<widget> p( new widget(…) );  
  my_class x( new widget() );  
  …  
} // automatic destruction and deallocation for both widget objects  
  // automatic exception safety, as if “finally { p->dispose(); x.w.dispose(); }”  
  
```  
  
 始终一次性将所有新资源到拥有它的其他对象。  
  
```cpp  
void g() {  
  other_class y( OpenFile() );  
  …  
} // automatic closing and release for file resource  
  // automatic exception safety, as if “finally { y.file.dispose(); }”  
  
```  
  
## 请参阅  
 [欢迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)