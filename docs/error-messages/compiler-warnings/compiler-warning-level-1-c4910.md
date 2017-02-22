---
title: "编译器警告（等级 1）C4910 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4910"
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器警告（等级 1）C4910
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\<identifier\>”: “\_\_declspec\(dllexport\)”和“extern”在显式实例化上不兼容  
  
 名为 *\<identifier\>* 的显式模板实例化由 `__declspec(dllexport)` 和 `extern` 关键字修改。 但是，这些关键字互斥。`__declspec(dllexport)` 关键字表示实例化模板类，而 `extern` 关键字表示不要自动实例化模板类。  
  
## 请参阅  
 [显式实例化](../../cpp/explicit-instantiation.md)   
 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)   
 [常规规则和限制](../../cpp/general-rules-and-limitations.md)