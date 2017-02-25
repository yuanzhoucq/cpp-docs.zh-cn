---
title: "编译器错误 C3816 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3816"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3816"
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3816
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declaration”以前是用不同的托管或 WinRT 修饰符声明或定义的  
  
 前向声明和实际声明要求特性声明中不存在任何冲突或不一致。  
  
 下面的示例生成 C3816，并演示如何修复此错误：  
  
```  
// C3816a.cpp  
// compile with: /clr /c  
class C1;  
// try the following line instead  
// ref class C1;  
  
ref class C1{  // C3816, forward declaration does not use ref  
};  
```