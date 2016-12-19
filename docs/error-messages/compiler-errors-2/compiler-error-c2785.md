---
title: "编译器错误 C2785 | Microsoft Docs"
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
  - "C2785"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2785"
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2785
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declaration1”和“declaration2”具有不同的返回类型  
  
 函数模板专用化的返回类型与主函数模板的返回类型不同。  
  
### 更正此错误  
  
1.  请对函数模板所有专用化的一致性进行检查。  
  
## 示例  
 下面的示例生成 C2785：  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```