---
title: "编译器警告（等级 1）C4027 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4027"
ms.assetid: f30d57b9-20c4-4284-8686-566d9f0ca7fc
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未用形参表声明的函数  
  
 函数声明没有形参，但在函数定义中有形参或在调用中有实参。 对此函数的后续调用假定该函数采用函数定义或调用中找到的类型的实参。