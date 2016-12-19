---
title: "编译器警告（等级 4）C4565 | Microsoft Docs"
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
  - "C4565"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4565"
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4565
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 重定义；该符号以前用 \_\_declspec\(modifier\) 声明过  
  
 已重定义或重新声明符号，并且与第一次定义或声明不同，第二次定义或声明不具有 `__declspec` 修饰符 \(***modifier***\)。  此警告是信息式的。  若要修复此警告，请删除其中一个定义。  
  
 下面的示例生成 C4565：  
  
```  
// C4565.cpp  
// compile with: /W4 /LD  
__declspec(noalias) void f();  
void f();   // C4565  
```