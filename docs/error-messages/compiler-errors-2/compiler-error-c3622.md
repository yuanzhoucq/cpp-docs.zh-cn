---
title: "编译器错误 C3622 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3622"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3622"
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3622
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 声明为“keyword”的类无法实例化  
  
 尝试实例化标记为 [abstract](../../windows/abstract-cpp-component-extensions.md)（或 [\_\_abstract](../../misc/abstract.md)）的类。  标记为抽象的类可以是基类，但不能进行实例化。  
  
## 示例  
 下面的示例生成 C3622。  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  
  
## 示例  
 下面的示例生成 C3622。  
  
```  
// C3622_b.cpp  
// compile with: /clr:oldSyntax  
__abstract class a {  
};  
int main() {  
   a aa;   // C3622  
}  
```