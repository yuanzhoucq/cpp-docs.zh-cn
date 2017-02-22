---
title: "编译器警告（等级 3）C4580 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4580"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4580"
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 3）C4580
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\[attribute\] 已弃用；改为指定 System::Attribute 或 Platform::Metadata 作为基类  
  
 [attribute](../../windows/attribute.md) 不再是创建用户定义的特性的首选语法。  有关详细信息，请参阅[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。  对于 CLR 代码，请从 [System::Attribute](assetId:///System::Attribute?qualifyHint=False&autoUpgrade=True) 派生特性。  对于 Windows 运行时代码，请从 `Platform::Metadata` 派生特性。  
  
## 示例  
 下面的示例将生成 C3454，并演示如何修复此错误。  
  
```  
// C4580.cpp  
// compile with: /W3 /c /clr  
[attribute]   // C4580  
public ref class Attr {  
public:  
   int m_t;  
};  
  
public ref class Attr2 : System::Attribute {  
public:  
   int m_t;  
};  
```