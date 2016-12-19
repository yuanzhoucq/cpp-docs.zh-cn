---
title: "编译器警告（等级 4）C4032 | Microsoft Docs"
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
  - "C4032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4032"
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提升后形参“number”具有不同的类型  
  
 通过默认提升，参数类型与以前声明中的类型不兼容。  
  
 这是 ANSI C \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 中的一个错误，也是 Microsoft 扩展 \(\/Ze\) 下的一个警告。  
  
## 示例  
  
```  
// C4032.c  
// compile with: /W4  
void func();  
void func(char);   // C4032, char promotes to int  
  
int main()  
{  
}  
```