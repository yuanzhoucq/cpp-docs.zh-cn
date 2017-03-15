---
title: "编译器警告（等级 1）C4091 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4091"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4091"
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4091
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“keyword”: 没有声明变量时忽略“type”的左侧  
  
 编译器检测到用户可能要声明一个变量，但是编译器无法声明该变量。  
  
## 示例  
 用户定义的类型声明开始处的 `__declspec` 特性适用于该类型的变量。  C4091 指示未声明任何变量。  下面的示例生成 C4091。  
  
```  
// C4091.cpp  
// compile with: /W1 /c  
__declspec(dllimport) class X {}; // C4091  
  
// __declspec attribute applies to varX  
__declspec(dllimport) class X2 {} varX;  
  
// __declspec attribute after the class or struct keyword   
// applies to user defined type  
class __declspec(dllimport) X3 {};  
```  
  
## 示例  
 如果标识符是 typedef，则它不能同时是变量名称。  下面的示例生成 C4091。  
  
```  
// C4091_b.cpp  
// compile with: /c /W1 /WX  
#define LIST 4  
typedef struct _LIST {} LIST;   // C4091  
```