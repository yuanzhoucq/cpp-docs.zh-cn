---
title: "编译器错误 C3161 | Microsoft Docs"
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
  - "C3161"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3161"
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3161
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“interface”: 在接口中的嵌套类、结构、联合或接口非法；在类、结构或联合中的嵌套接口非法  
  
 [\_\_interface](../../cpp/interface.md) 只能出现在全局范围或命名空间内。  类、结构或联合不能出现在接口中。  
  
## 示例  
 下面的示例生成 C3161。  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```