---
title: "编译器错误 C3296 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3296"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3296"
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C3296
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“property”：已存在同名属性  
  
 编译器遇到具有相同名称的多个属性。 类型中的每个属性均必须具有唯一名称。  
  
 有关详细信息，请参阅[属性](../../windows/property-cpp-component-extensions.md)。  
  
## 示例  
 以下示例生成 C3296。  
  
```  
// C3296.cpp // compile with: /clr /c using namespace System; ref class R { public: property int MyProp[int] { int get(int); } property String^ MyProp[int] { void set(int, String^); }   // C3296 };  
```