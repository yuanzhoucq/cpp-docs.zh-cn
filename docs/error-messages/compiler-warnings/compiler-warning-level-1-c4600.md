---
title: "编译器警告（等级 1）C4600 | Microsoft Docs"
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
  - "C4600"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4600"
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4600
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma“macro name”: 应输入有效的非空字符串  
  
 在您用 [pop\_macro](../../preprocessor/pop-macro.md) 或 [push\_macro](../../preprocessor/push-macro.md) 推入或弹出宏名时，不能指定空字符串。  
  
 下面的示例生成 C4600：  
  
```  
// C4600.cpp  
// compile with: /W1  
int main()  
{  
   #pragma push_macro("")   // C4600 passing an empty string  
}  
```