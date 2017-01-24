---
title: "CLS 符合性警告 CLS09911 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS09911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS09911"
ms.assetid: 8cc0b0c0-a823-4392-9bf9-4d12242ef451
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS09911
泛型类型不符合 CLS  
  
 符合 CLS 的类型不能同时是泛型类型。  有关 Visual C\+\+ 中泛型的详细信息，请参阅[对 C\+\+ 中泛型的支持](../windows/generics-cpp-component-extensions.md)。  
  
 有关公共语言子集 \(CLS\) 符合性检查的详细信息，请参阅[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下示例生成 CLS09911：  
  
```  
// CLS09911.cpp // compile with: /clr /LD using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; generic <class T> public ref class Five {   // CLS09911 };  
  
```