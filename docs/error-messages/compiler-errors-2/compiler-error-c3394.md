---
title: "编译器错误 C3394 | Microsoft Docs"
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
  - "C3394"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3394"
ms.assetid: 4e025d79-27ba-43c8-b0d9-839ecef98126
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3394
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

constraint 子句有语法错误：应为类型却发现“identifier”  
  
 约束格式不正确。  有关详细信息，请参阅[约束](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C3394：  
  
```  
// C3394.cpp // compile with: /clr /c ref class MyClass {}; ref class R { generic<typename T> where T : static   // C3394 // try the following line instead // where T : MyClass void f() {} };  
```