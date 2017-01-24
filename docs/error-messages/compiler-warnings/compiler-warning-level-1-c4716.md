---
title: "编译器警告（等级 1）C4716 | Microsoft Docs"
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
  - "C4716"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4716"
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4716
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”必须返回值  
  
 给定函数不返回值。  
  
 只有返回类型为 void 的函数才能使用不伴随返回值的返回命令。  
  
 当调用该函数时，将返回未定义的值。  
  
 此警告自动升级为错误。  如果希望修改此行为，请使用 [\#pragma warning](../../preprocessor/warning.md)。  
  
 下面的示例生成 C4716：  
  
```  
// C4716.cpp  
// compile with: /c /W1  
// C4716 expected  
#pragma warning(default:4716)  
int test() {  
   // uncomment the following line to resolve  
   // return 0;  
}  
```