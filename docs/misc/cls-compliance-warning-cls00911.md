---
title: "CLS 遵从性警告 CLS00911 | Microsoft Docs"
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
  - "CLS00911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00911"
ms.assetid: d1a4721a-a3a6-4de0-bc14-a0b3c5e6dd78
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS00911
枚举的文本静态字段需具有枚举本身的类型  
  
 确保枚举的文本静态字段具有枚举本身的类型。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下声明（使用 MSIL 程序集语言）显示可能导致 CLS00911 的原因：  
  
```  
.assembly extern legacy library mscorlib {} .assembly legacy library Out {} .namespace Test { .class public auto ansi sealed MyEnum1 extends [mscorlib]System.Enum { .field public specialname rtspecialname int32 value__ .field public static literal uint8 One = uint8(0x1) } // end of class MyEnum1 }  
```  
  
 通过使枚举字段成为枚举类型，可解决此警告：  
  
```  
.assembly extern legacy library mscorlib {} .assembly legacy library Out {} .namespace Test { .class public auto ansi sealed MyEnum1 extends [mscorlib]System.Enum { .field public specialname rtspecialname int32 value__ .field public static literal valuetype Test.MyEnum1 One = uint8(0x1) } // end of class MyEnum1 }  
```