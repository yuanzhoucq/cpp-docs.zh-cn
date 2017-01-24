---
title: "编译器警告（等级 4）C4634 | Microsoft Docs"
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
  - "C4634"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4634"
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4634
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文档注释：不能应用：原因  
  
 XML 文档标记不能应用于所有 C\+\+ 构造。  例如，无法将文档注释添加到命名空间或模板中。  
  
 有关更多信息，请参见[XML 文档](../../ide/xml-documentation-visual-cpp.md)。  
  
## 示例  
 下面的示例生成 C4634。  
  
```  
// C4634.cpp // compile with: /W4 /doc /c /// This is a namespace.   // C4634 namespace hello { class MyClass  {}; };  
```  
  
## 示例  
 下面的示例生成 C4634。  
  
```  
// C4634_b.cpp // compile with: /W4 /doc /c /// This is a template.   // C4634 template <class T> class MyClass  {};  
```