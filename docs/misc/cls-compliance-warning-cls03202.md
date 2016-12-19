---
title: "CLS 遵从性警告 CLS03202 | Microsoft Docs"
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
  - "CLS03202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03202"
ms.assetid: 2219c86c-9276-4244-a2ff-bce578c4d65f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS03202
事件的 add 和 remove 方法均应采用一个参数，该参数的类型定义了事件的类型，且应派生自 System.Delegate  
  
 事件的 add 和 remove 方法均应采用一个参数，该参数的类型定义了事件的类型，且应派生自 System.Delegate。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下函数声明（使用 MSIL 程序集语言）显示可能导致 CLS03202 的原因：  
  
```  
// bad .method public specialname instance void add_MyEvent(class MyDelegate __unnamed000, int32 __extra) cil managed {}  
```  
  
 如果事件访问器仅采用一个参数，则可以解决此警告：  
  
```  
.method public specialname instance void add_MyEvent(class MyDelegate __unnamed000) cil managed {}  
```