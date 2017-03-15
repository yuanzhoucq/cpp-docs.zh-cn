---
title: "Compiler Error C3209 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3209"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3209"
ms.assetid: 1de44e39-69d1-4894-8f89-ff92136e8e5d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Compiler Error C3209
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：泛型类必须是托管或 WinRT 类  
  
 泛型类必须是托管类或 Windows 运行时类。  
  
 下面的示例生成 C3209，并演示如何修复此错误：  
  
```  
// C3209.cpp  
// compile with: /clr  
generic <class T>  
class C {};   // C3209  
  
// OK - ref class can be generic  
generic <class T>  
ref class D {};  
```