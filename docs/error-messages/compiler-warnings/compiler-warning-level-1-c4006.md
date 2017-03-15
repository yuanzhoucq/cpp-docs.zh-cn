---
title: "编译器警告（等级 1）C4006 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4006"
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#undef 应输入标识符  
  
 `#undef` 指令未指定要取消定义的标识符。 指令被忽略。 若要解决此警告，请确保指定一个标识符。 以下示例生成 C4006：  
  
```  
// C4006.cpp // compile with: /W1 #undef   // C4006 // try.. // #undef TEST int main() { }  
```