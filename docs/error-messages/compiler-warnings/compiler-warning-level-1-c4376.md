---
title: "编译器警告（等级 1）C4376 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4376"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4376"
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4376
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不再支持访问说明符“old\_specifier:”: 请改用“new\_specifier:”  
  
 有关指定的元数据类型和成员可访问性的更多信息，请参阅[类型可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 和 [成员可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) 在 [如何：定义和使用类和结构](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C4376。  
  
```  
// C4376.cpp  
// compile with: /clr /W1 /c  
public ref class G {  
public public:   // C4376  
   void m2();  
};  
  
public ref class H {  
public:   // OK  
   void m2();  
};  
```