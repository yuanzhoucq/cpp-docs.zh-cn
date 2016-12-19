---
title: "编译器错误 CS1056 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1056"
ms.assetid: bf66d164-ab5b-4181-b93e-a1d29620b4d2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1056
意外的字符“character”  
  
 C\# 编译器遇到了意外的字符，并且不能识别当前正在处理的标记。 例如，如果编译器在处理标识符过程中遇到欧洲字符，它将无法将标识符分类，因为欧洲字符仅在字符串内有效，且编译器知道它没在处理字符串。