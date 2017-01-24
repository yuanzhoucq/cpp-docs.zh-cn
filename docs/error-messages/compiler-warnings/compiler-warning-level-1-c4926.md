---
title: "编译器警告（等级 1）C4926 | Microsoft Docs"
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
  - "C4926"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4926"
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4926
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：已定义符号：忽略特性  
  
 已找到前向声明，但已存在具有相同名称的特性化的构造。 忽略前向声明的特性。  
  
 下面的示例生成 C4926：  
  
```  
// C4926.cpp // compile with: /W1 [module(name="MyLib")]; [coclass] struct a { }; [coclass] struct a;   // C4926 int main() { }  
```