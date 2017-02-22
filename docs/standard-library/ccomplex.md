---
title: "&lt;ccomplex&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<ccomplex>"
dev_langs: 
  - "C++"
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;ccomplex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含 STL 标头 [\<complex\>](../standard-library/complex.md)，它可有效地包含标准 C 库标头 \<complex.h\>，并将关联名称添加到 `std` 命名空间。  
  
## 语法  
  
```cpp  
  
#include <ccomplex>  
  
```  
  
## 备注  
 包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。  
  
 未在 `std` 命名空间中定义 \<complex.h\> 中声明的名称 `clog`，因为这可能会与 [\<iostream\>](../standard-library/iostream.md) 中声明的 `clog` 发生冲突。  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [STL 概述](../standard-library/cpp-standard-library-overview.md)