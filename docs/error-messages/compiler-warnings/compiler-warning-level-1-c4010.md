---
title: "编译器警告（等级 1）C4010 | Microsoft Docs"
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
  - "C4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4010"
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

单行注释包含行继续符  
  
 由 \/\/ 引入的单行注释包含一个反斜杠 \(\\\)，该反斜杠用作行继续符。  编译器将下一行视为单行注释的继续，将其作为注释处理。  
  
 有些语法导向的编辑器并不把继续符后面的一行指示为注释。  请忽略导致此警告的任何行的语法着色。  
  
 下面的示例生成 C4010：  
  
```  
// C4010.cpp  
// compile with: /WX  
int main() {  
   // the next line is also a comment because of the backslash \  
   int a = 3; // C4010  
   a++;  
}  
```