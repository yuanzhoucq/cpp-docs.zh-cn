---
title: "编译器警告（等级 1）C4393 | Microsoft Docs"
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
  - "C4393"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4393"
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4393
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”: 常量不会影响 literal 数据成员；已忽略  
  
 [文本](../../windows/literal-cpp-component-extensions.md) 数据成员指定为常数。由于 literal 数据成员意味着常量，您无需将常量添加到声明。  
  
 下面的示例生成 C4393：  
  
```  
// C4393.cpp  
// compile with: /clr /W1 /c  
ref struct Y1 {  
   literal const int staticConst = 10;   // C4393  
   literal int staticConst2 = 10;   // OK  
};  
```