---
title: "编译器错误 C3755 | Microsoft Docs"
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
  - "C3755"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3755"
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3755
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“delegate”: 不能定义委托  
  
 可以声明 [委托](../../windows/delegate-cpp-component-extensions.md)，但不能定义它。  
  
## 示例  
 下面的示例生成 C3755。  
  
```  
// C3755.cpp  
// compile with: /clr /c  
delegate void MyDel() {};   // C3755  
```  
  
## 示例  
 如果尝试创建委托模板，也可能发生 C3755。  下面的示例生成 C3755。  
  
```  
// C3755_b.cpp  
// compile with: /clr /c  
ref struct R {  
   template<class T>  
   delegate void D(int) {}   // C3755  
};  
```