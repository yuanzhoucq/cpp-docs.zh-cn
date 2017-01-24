---
title: "编译器错误 C2599 | Microsoft Docs"
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
  - "C2599"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2599"
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2599
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“enum”: 不允许枚举类型的前向声明  
  
 编译器不再支持托管枚举的前向声明。  
  
 在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 下不允许的枚举类型的前向声明。  
  
 下面的示例生成 C2599：  
  
```  
// C2599.cpp  
// compile with: /clr /c  
enum class Status;   // C2599  
  
enum class Status2 { stop2, hold2, go2};   
  
ref struct MyStruct {  
   // Delete the following line to resolve.  
   Status m_status;  
  
   Status2 m_status2;   // OK  
};  
  
enum class Status { stop, hold, go };  
```