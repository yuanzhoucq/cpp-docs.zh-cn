---
title: "编译器错误 C2535 | Microsoft Docs"
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
  - "C2535"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2535"
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2535
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 已经定义或声明成员函数  
  
 在重载函数的多个定义或声明中使用同一形参表可导致此错误。  
  
 如果因为 Dispose 函数获得 C2535 ，有关详细信息请参阅[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) 。  
  
 如果要编译 ATL 项目，请参见知识库文章 Q241852。  
  
 下面的示例生成 C2535：  
  
```  
// C2535.cpp  
// compile with: /c  
class C {  
public:  
   void func();   // forward declaration  
   void func() {}   // C2535  
};  
```