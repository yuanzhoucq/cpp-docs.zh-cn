---
title: "编译器错误 C3458 | Microsoft Docs"
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
  - "C3458"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3458"
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3458
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“attribute1”: 已为“construct”指定特性“attribute2”  
  
 为同一个构造指定了两个互相排斥的特性。  
  
## 示例  
 下面的示例生成 C3458  
  
```  
// C3458.cpp // compile with: /clr /c [System::Reflection::DefaultMember("Chars")] public ref class MyString { public: [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458 property char default[int] { char get(int index); void set(int index, char c); } };  
```