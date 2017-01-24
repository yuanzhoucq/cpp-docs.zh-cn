---
title: "错误 C1197 | Microsoft Docs"
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
  - "C1197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1197"
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法引用“mscorlib.dll\_1”，因为程序已引用“mscorlib.dll\_2”  
  
 编译器与公共语言运行时的版本匹配。但是，尝试从早期版本引用公共语言运行时文件的版本。  
  
 若要消除此错误，只能从与编译所用的 Visual C\+\+ 版本一起提供的公共语言运行时版本中引用文件。  
  
## 示例  
 下面的示例生成 C1197：  
  
```  
// C1197.cpp  
// compile with: /clr /c  
// processor: x86  
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197  
// try the following line instead  
// #using "mscorlib.dll"  
```