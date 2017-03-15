---
title: "编译器警告 C4694 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4694"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4694"
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器警告 C4694
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class\_1”：密封的抽象类不能有基类“base\_class”  
  
 一个抽象密封类不能继承自引用类型；一个密封抽象类既不能实现基类函数，也不能用作基类。  
  
 有关详细信息，请参阅[abstract](../../windows/abstract-cpp-component-extensions.md)、[sealed](../../windows/sealed-cpp-component-extensions.md)和[类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## 示例  
 以下示例生成 C4694。  
  
```  
// C4694.cpp // compile with: /c /clr ref struct A {}; ref struct B sealed abstract : A {};   // C4694  
```