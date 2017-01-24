---
title: "CLS 符合性警告 CLS01603 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01603"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01603"
ms.assetid: 608ff6e6-8669-4cc7-a85f-5b6915ee38d5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01603
数组应具有符合 CLS 类型的元素，且数组的所有维度的下限应为零  
  
 数组应具有符合 CLS 类型的元素，且数组的所有维度的下限应为零。 各重载间只需区别：项是数组还是数组的元素类型。 当重载基于两个或更多数组类型时，元素类型应为命名类型。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下面的示例生成 CLS01603：  
  
```  
// CLS01603.cpp // compile with: /clr /LD // CLS01603 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(false)] public delegate void MyDelegate(Object ^ sender, EventArgs^ e); public delegate void MyDelegate2(Object ^ sender, EventArgs^ e); public ref struct One { array<MyDelegate^>^ MyArray;   // CLS01603 array<MyDelegate2^>^ MyArray2;   // OK };  
```