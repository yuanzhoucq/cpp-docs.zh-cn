---
title: "编译器警告（等级 4）C4670 | Microsoft Docs"
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
  - "C4670"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4670"
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4670
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：该基类不可访问  
  
 要在 **try** 块中引发的对象的指定基类不可访问。 不能实例化引发的对象。 检查基类继承了正确的访问说明符。  
  
 下面的示例生成 C4670：  
  
```  
// C4670.cpp // compile with: /EHsc /W4 class A { }; class B : /* public */ A { } b;   // inherits A with private access by default int main() { try { throw b;   // C4670 } catch( B ) { } }  
```