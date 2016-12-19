---
title: "编译器错误 C3385 | Microsoft Docs"
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
  - "C3385"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3385"
ms.assetid: 5f1838c1-986e-47db-8dbc-e06976b83cf3
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3385
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class::function”：具有 DllImport 自定义特性的函数不能返回类实例  
  
 被定义为位于使用 `DllImport` 特性指定的 .dll 文件中的函数不能返回类的实例。  
  
 以下示例生成 C3385：  
  
```  
// C3385.cpp // compile with: /clr /c using namespace System; using namespace System::Runtime::InteropServices; struct SomeStruct1 {}; public ref struct Wrap { [ DllImport("somedll.dll", CharSet=CharSet::Unicode) ] static SomeStruct1 f1([In, Out] SomeStruct1 *pS);   // C3385 };  
```  
  
 以下示例生成 C3385：  
  
```  
// C3385_2.cpp // compile with: /clr:oldSyntax /c using namespace System; using namespace System::Runtime::InteropServices; struct SomeStruct1 {}; public __gc struct Wrap { [ DllImport("somedll.dll", CharSet=CharSet::Unicode) ] static SomeStruct1 f1([In, Out] SomeStruct1 *pS);   // C3385 };  
```