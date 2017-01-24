---
title: "编译器警告（等级 3）C4398 | Microsoft Docs"
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
  - "C4398"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4398"
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4398
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“variable”: per\-process 全局对象可能无法与多个 appdomain 一起正常工作；请考虑使用 \_\_declspec\(appdomain\)  
  
 在本机类型中采用 [\_\_clrcall](../../cpp/clrcall.md) 调用约定的虚函数可导致创建每个应用程序域 vtable。  在多个应用程序域中使用时，此变量可能无法正常工作。  
  
 通过使用 **\/clr:pure**（默认情况下对每个 appdomain 生成全局变量）进行编译或通过显式标记变量 `__declspec(appdomain)` 可解决此警告。  
  
 有关更多信息，请参见[appdomain](../../cpp/appdomain.md)和[应用程序域和 Visual C\+\+](../../dotnet/application-domains-and-visual-cpp.md)。  
  
## 示例  
 下面的示例生成 C4398。  
  
```  
// C4398.cpp  
// compile with: /clr /W3 /c  
struct S {  
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall  
};  
  
S glob_s;   // C4398  
__declspec(appdomain) S glob_s2;   // OK  
```