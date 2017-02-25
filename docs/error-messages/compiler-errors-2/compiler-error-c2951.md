---
title: "编译器错误 C2951 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2951"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2951"
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2951
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类型声明只能在全局、命名空间或类范围内使用  
  
 不能在全局或命名空间范围之外声明泛型类或模板类。  如果在包含文件中进行泛型声明或模板声明，请确保包含文件位于全局范围内。  
  
 下面的示例生成 C2951：  
  
```  
// C2951.cpp  
template <class T>  
class A {};  
  
int main() {  
   template <class T>   // C2951  
   class B {};  
}  
```  
  
 使用以下泛型时也可能发生 C2951 错误：  
  
```  
// C2951b.cpp  
// compile with: /clr /c  
  
// OK  
generic <class T>   
ref class GC { };  
  
int main() {  
   generic <class T> ref class GC2 {};   // C2951  
}  
```