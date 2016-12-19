---
title: "编译器错误 C2011 | Microsoft Docs"
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
  - "C2011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2011"
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：“type”类型重定义  
  
 标识符已定义为 `type`。  检查标识符的重定义。  
  
 如果不止一次将头文件或类型库导入同一个文件，则也有可能生成 C2011。  若要防止多次包含头文件中定义的类型，可使用头文件中的 include guards 或`#pragma` [once](../../preprocessor/once.md) 指令。  
  
 如果需要查找重定义的类型的初始声明，则可以使用 [\/P](../../build/reference/p-preprocess-to-a-file.md) 编译器标志生成传递给编译器的预处理输出。  你可以使用文本搜索工具在输出文件中查找重定义的标识符的实例。  
  
 下面的示例生成了 C2011 并演示了修复此错误的一种方法：  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```