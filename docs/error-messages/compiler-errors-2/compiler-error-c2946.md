---
title: "编译器错误 C2946 | Microsoft Docs"
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
  - "C2946"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2946"
ms.assetid: c86dfbfc-7702-4f09-8a53-d205710e99c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2946
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显式实例化；“类”不是模板类专用化  
  
 不能显式实例化非模板化的类。  
  
## 示例  
 下面的示例生成 C2946。  
  
```  
// C2946.cpp class C {}; template C;  // C2946 int main() {}  
```