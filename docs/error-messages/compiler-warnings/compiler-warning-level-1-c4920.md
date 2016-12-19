---
title: "编译器警告（等级 1）C4920 | Microsoft Docs"
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
  - "C4920"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4920"
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4920
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

enum enum member member\=value 在 enum enum 中被视为 member\=value  
  
 如果传递到 \#import 的 .tlb 具有在两个或更多的枚举中定义的相同符号，则此警告指示后续的相同符号被忽略，且会在 .tlh 文件中被注释掉。  
  
 假定 .tlb 包含：  
  
```  
library MyLib { typedef enum { enumMember = 512 } AProblem; typedef enum { enumMember = 1024 } BProblem; };  
```  
  
 以下示例生成 C4920，  
  
```  
// C4920.cpp // compile with: /W1 #import "t4920.tlb"   // C4920 int main() { }  
```