---
title: "编译器警告（等级 1）C4144 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4144"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4144"
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4144
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“expression”: 关系表达式用作 switch 表达式  
  
 指定的关系表达式被用作 [switch](../../cpp/switch-statement-cpp.md) 语句的控制表达式。  将向关联的 case 语句提供布尔值。  下面的示例生成 C4144：  
  
```  
// C4144.cpp  
// compile with: /W1  
int main()  
{  
   int i = 0;  
   switch(!i) {   // C4144, remove the ! to resolve  
      case 1:  
         break;  
      default:  
         break;  
   }  
}  
```