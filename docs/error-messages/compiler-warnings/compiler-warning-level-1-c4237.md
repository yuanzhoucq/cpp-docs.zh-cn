---
title: "编译器警告（等级 1）C4237 | Microsoft Docs"
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
  - "C4237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4237"
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

目前还不支持“keyword”关键字，但已保留该关键字供将来使用  
  
 C\+\+ 规范中的关键字未在 Visual C\+\+ 编译器中实现，但是该关键字不能用作用户定义的符号。  
  
 下面的示例生成 C4237：  
  
```  
// C4237.cpp  
// compile with: /W1 /c  
int export;   // C4237  
```