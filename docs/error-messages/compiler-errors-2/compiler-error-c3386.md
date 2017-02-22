---
title: "Compiler Error C3386 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3386"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3386"
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Compiler Error C3386
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: \_\_declspec\(dllexport\)\/\_\_declspec\(dllimport\) 不适用于托管或 WinRT 类型  
  
 `dllimport` 和 [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` 修饰符都不是有效的托管或 Windows 运行时类型。  
  
 下面的示例生成 C3386，并演示如何修复此错误：  
  
```  
// C3386.cpp  
// compile with: /clr /c  
ref class __declspec(dllimport) X1 {   // C3386  
// try the following line instead  
// ref class X1 {  
};  
```