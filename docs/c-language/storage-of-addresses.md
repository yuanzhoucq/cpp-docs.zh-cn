---
title: "地址存储 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "地址 [C++], 存储"
  - "存储 [C++], 地址"
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 地址存储
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

地址所需的存储量和该地址的含义取决于编译器的实现。  指向不同类型的指针不能保证具有相同的长度。  因此，**sizeof\(char \*\)** 不必与 **sizeof\(int \*\)** 相等。  
  
 **Microsoft 专用**  
  
 对于 Microsoft C 编译器，**sizeof\(char \*\)** 与 **sizeof\(int \*\)** 相等。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [指针声明](../c-language/pointer-declarations.md)