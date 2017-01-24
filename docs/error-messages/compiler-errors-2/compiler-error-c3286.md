---
title: "编译器错误 C3286 | Microsoft Docs"
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
  - "C3286"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3286"
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3286
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“specifier”：迭代变量不能包含任何存储类说明符  
  
 详细信息，请参阅 [\(NOTINBUILD\)存储类说明符](http://msdn.microsoft.com/zh-cn/10b3d22d-cb40-450b-994b-08cf9a211b6c)。  
  
 有关更多信息，请参见[for each，in](../../dotnet/for-each-in.md)。  
  
## 示例  
 以下示例生成 C3286：  
  
```  
// C3286.cpp // compile with: /clr int main() { array<int> ^p = { 1, 2, 3 }; for each (static int i in p) {}   // C3286 for each (int j in p) {}   // OK }  
```