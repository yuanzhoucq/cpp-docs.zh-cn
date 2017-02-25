---
title: "静态存储类说明符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "静态存储类说明符"
  - "静态变量, 说明符"
  - "存储类, static"
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 静态存储类说明符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 **static** 存储类说明符在内部级别声明的变量具有全局生存期，但它仅在声明它的块中可见。  对于常量字符串，使用 **static** 会很有用，因为它减少了频繁初始化经常调用的函数的开销。  
  
## 备注  
 如果不显式初始化 **static** 变量，则默认情况下它将初始化为 0。  在函数内，**static** 会导致存储被分配并用作定义。  内部静态变量仅提供对单个函数可见的私有永久存储。  
  
## 请参阅  
 [Static](../misc/static-cpp.md)