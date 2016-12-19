---
title: "Compiler Error C2384 | Microsoft Docs"
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
  - "C2384"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2384"
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C2384
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“membe”：不能对托管类或 WinRT 类的成员应用 \_\_declspec\(thread\)  
  
 [线程](../../cpp/thread.md) `__declspec` 修饰符不能用于托管类或 Windows 运行时类的成员。  
  
 托管代码中的静态线程本地存储仅可用于静态加载的 DLL（进程启动时，必须以静态方式加载该 DLL）。  Windows 运行时不支持线程本地存储。  
  
 下面的行生成 C2384 并演示如何在 C\+\+\/CLI 代码中修复此错误：  
  
```  
// C2384.cpp  
// compile with: /clr /c  
public ref class B {  
public:  
   __declspec( thread ) static int tls_i = 1;   // C2384  
  
   // OK - declare with attribute instead  
   [System::ThreadStaticAttribute]  
   static int tls_j;  
};  
```