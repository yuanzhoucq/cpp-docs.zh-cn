---
title: "编译器错误 C3295 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3295"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3295"
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 编译器错误 C3295
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\#pragma pragma”只能在全局范围或命名空间范围上使用  
  
 部分杂注不能在函数中使用。  有关更多信息，请参见[Pragma 指令和 \_\_Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。  
  
## 示例  
 以下示例生成 C3295。  
  
```  
// C3295.cpp int main() { #pragma managed   // C3295 }  
```