---
title: "编译器错误 C2989 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2989"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2989"
ms.assetid: 936303d8-eb3b-4746-82ec-2f18020a6f64
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2989
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class” : 类类型已声明为非类类型  
  
 类泛型或模板重定义非模板或非泛型类。  检查头文件中是否有冲突。  
  
 如果您在使用类模板部分专用化，请参见知识库文章 Q240866。  
  
 下面的示例生成 C2989：  
  
```  
// C2989.cpp  
// compile with: /c  
class C{};  
  
template <class T>  
class C{};  // C2989  
class C2{};  
```  
  
 使用泛型时也可能发生 C2989：  
  
```  
// C2989b.cpp  
// compile with: /clr /c  
ref class GC1;  
  
generic <typename T> ref class GC1;   // C2989  
template <typename T> ref class GC2;  
  
generic <typename T> ref class GC2;   // C2989  
generic <typename T> ref class GCb;  
template <typename T> ref class GC2;  
generic <typename T> ref class GCc;  
```