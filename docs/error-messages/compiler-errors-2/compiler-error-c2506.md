---
title: "编译器错误 C2506 | Microsoft Docs"
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
  - "C2506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2506"
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”:“\_\_declspec\(modifier\)”不能应用于此符号  
  
 不能为托管类的静态成员声明 per\-process 或 per\-appdomain。  
  
 有关更多信息，请参见[appdomain](../../cpp/appdomain.md)。  
  
## 示例  
 下面的示例生成 C2506。  
  
```  
// C2506.cpp  
// compile with: /clr /c  
ref struct R {  
   __declspec(process) static int n;   // C2506  
   int o;   // OK  
};  
```