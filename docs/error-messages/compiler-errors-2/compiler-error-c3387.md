---
title: "Compiler Error C3387 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3387"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3387"
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Compiler Error C3387
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”：\_\_declspec\(dllexport\)\/\_\_declspec\(dllimport\) 不能应用于托管或 WinRT 类型的成员  
  
 `dllimport` 和 [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` 修饰符在托管或 Windows 运行时类型的成员上都无效。  
  
 下面的示例将生成 C3387，并演示如何修复此错误：  
  
```  
// C3387a.cpp  
// compile with: /clr /c  
ref class X2 {  
   void __declspec(dllexport) mf() {   // C3387  
   // try the following line instead  
   // void mf() {  
   }  
};  
```