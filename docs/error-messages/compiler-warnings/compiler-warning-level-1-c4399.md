---
title: "编译器警告（等级 1）C4399 | Microsoft Docs"
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
  - "C4399"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4399"
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4399
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 在使用 \/clr:pure 进行编译时，per\-process 符号不应该用 \_\_declspec\(dllimport\)进行标记  
  
 本机映像或包含本机和 CLR 构造的映像中的数据无法导入纯映像中。  若要解决此警告，请使用 **\/clr**（而不是 **\/clr:pure**）进行编译，或者删除 `__declspec(dllimport)`。  
  
## 示例  
 下面的示例生成 C4399。  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```