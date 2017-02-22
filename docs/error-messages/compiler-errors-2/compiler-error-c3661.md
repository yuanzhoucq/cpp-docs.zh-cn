---
title: "编译器错误 C3661 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3661"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3661"
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3661
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显式重写列表没有发现任何要重写的方法  
  
 一个显式重写指定了一个或多个类型名称。但是，在与重写函数的签名匹配的类型中没有任何函数具有所需的签名。如果尝试基于类型名称重写，在指定的与重写函数的签名匹配的类型中必须有一个或多个虚函数。  
  
 有关更多信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。