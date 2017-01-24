---
title: "编译器错误 C2047 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2047"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2047"
ms.assetid: 686a5a81-3857-4753-84a0-5c2e7149cbee
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2047
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非法的 default  
  
 关键字 `default` 仅出现在 `switch` 语句中。  
  
 以下示例生成 C2047:  
  
```  
// C2047.cpp int main() { int i = 0; default:   // C2047 switch(i) { case 0: break; } }  
```  
  
 可能的解决方法：  
  
```  
// C2047b.cpp int main() { int i = 0; switch(i) { case 0: break; default: break; } }  
```