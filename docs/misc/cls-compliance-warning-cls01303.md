---
title: "CLS 符合性警告 CLS01303 | Microsoft Docs"
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
  - "CLS01303"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01303"
ms.assetid: a8aa0cda-a2dd-41da-bcc2-53221207ea70
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01303
符合 CLS 的文本必须具有在字段初始化元数据中指定的、与该文本（如果文本为枚举，则与基本类型）完全相同的值  
  
 通过使用字段初始化元数据指定文本静态值。 符合 CLS 的文本必须具有在字段初始化元数据中指定的、与该文本（如果文本为枚举，则与基本类型）完全相同的值。  
  
 确保字段文本具有与该文本（如果文本为枚举，则与基本类型）完全相同的类型。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下声明（使用 MSIL 程序集语言）显示可能导致 CLS01303 的原因：  
  
```  
.field public static literal char Field2 = int32(0x00000002)  
```  
  
 统一初始值设定项与文本的类型，即可解决此警告：  
  
```  
.field public static literal char Field2 = char(0x00000002)  
```