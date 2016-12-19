---
title: "编译器警告（等级 1）C4381 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4381"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4381"
ms.assetid: f67a6db3-b334-4b2e-8182-b30c7a3c7c32
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4381
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function1”: 非公共方法“function2”将不实现接口方法  
  
 类必须实现接口中的所有函数。  如果类的某个基类实现了该函数，则该类可以满足此条件。  但是，该函数必须作为公共函数来实现。