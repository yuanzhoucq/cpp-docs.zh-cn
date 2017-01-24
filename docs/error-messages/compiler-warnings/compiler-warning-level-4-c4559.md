---
title: "编译器警告（等级 4）C4559 | Microsoft Docs"
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
  - "C4559"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4559"
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4559
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 重定义；该函数获取 \_\_declspec\(modifier\)  
  
 函数被重定义或重新声明，在第二次定义或声明中添加了 \_\_**declspec** 修饰符 \(***modifier***\)。  此警告是信息式的。  若要修复此警告，请删除其中一个定义。  
  
 下面的示例生成 C4559：  
  
```  
// C4559.cpp  
// compile with: /W4 /LD  
void f();  
__declspec(noalias) void f();   // C4559  
```