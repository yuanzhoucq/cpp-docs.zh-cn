---
title: "编译器错误 C2555 | Microsoft Docs"
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
  - "C2555"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2555"
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2555
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class1::function1”: 重写虚函数返回类型有差异，且不是来自“class2::function2”的协变  
  
 虚函数和派生的重写函数具有相同的参数列表，但返回类型不同。  派生类中的重写函数不能仅在其返回类型方面与基类中的虚函数有差异。  
  
 若要解决此错误，在已调用虚函数后转换返回值。  
  
 如果用 \/clr 进行编译，也可能发生此错误。例如，Visual C\+\+ 等效于以下 C\# 声明：  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 为  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 有关 C2555 的更多信息，请参见知识库文章 Q240862。  
  
 下面的示例生成 C2555：  
  
```  
// C2555.cpp  
// compile with: /c  
struct X {  
   virtual void func();  
};  
struct Y : X {  
   char func();  // C2555  
   void func2();   // OK  
};  
```