---
title: "编译器警告 C4368 | Microsoft Docs"
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
  - "C4368"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4368"
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4368
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不能将“member”定义为托管“type”的成员: 不支持混合类型  
  
 不能在 CLR 类型中嵌入本机数据成员。  
  
 但是，可以将指针声明为本机类型，并可在托管类的构造函数、析构函数和终结器中控制该指针的生命周期。  有关详细信息，请参阅[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
 此警告始终按错误发出。  使用 [警告](../../preprocessor/warning.md) 杂注来禁用 C4368。  
  
## 示例  
 下面的示例生成 C4368。  
  
```  
// C4368.cpp  
// compile with: /clr /c  
struct N {};  
ref struct O {};  
ref struct R {  
    R() : m_p( new N ) {}  
    ~R() { delete m_p; }  
  
   property N prop;   // C4368  
   int i[10];   // C4368  
  
   property O ^ prop2;   // OK  
   N * m_p;   // OK  
};  
```