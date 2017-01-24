---
title: "编译器警告（等级 3）C4159 | Microsoft Docs"
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
  - "C4159"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4159"
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4159
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma pragma\(pop,...\): 将先前入栈的标识符“identifier”弹出栈  
  
 源代码包含带有杂注标识符的 **push** 指令，其后是不含标识符的 **pop** 指令。  结果 ***identifier*** 被弹出，以后使用 ***identifier*** 时可能导致意外行为。  
  
 若要避免该警告，请在 **pop** 指令中提供一个标识符。  例如：  
  
```  
// C4159.cpp  
// compile with: /W3  
#pragma pack(push, f)  
#pragma pack(pop)   // C4159  
  
// using the identifier resolves the warning  
// #pragma pack(pop, f)  
  
int main()  
{  
}  
```