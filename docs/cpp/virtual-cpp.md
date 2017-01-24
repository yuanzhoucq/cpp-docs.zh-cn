---
title: "virtual (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "virtual_cpp"
  - "virtual"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基类, virtual"
  - "虚拟基类, 声明"
  - "虚函数, 声明"
  - "virtual 关键字 [C++]"
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# virtual (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`virtual` 关键字声明一个虚拟函数或一个虚拟基类。  
  
## 语法  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### 参数  
 `type-specifiers`  
 指定此虚拟成员函数的返回类型。  
  
 `member-function-declarator`  
 声明一个成员函数。  
  
 `access-specifier`  
 定义对基类的访问级别（`public`、`protected` 或 `private`）。  可以在 `virtual` 关键字之前或之后显示。  
  
 `base-class-name`  
 标识一个以前声明的类类型。  
  
## 备注  
 有关详细信息，请参阅[虚拟函数](../cpp/virtual-functions.md)和[虚拟基类](../misc/virtual-base-classes.md)。  
  
 另请参阅以下关键字：[class](../cpp/class-cpp.md)、[private](../cpp/private-cpp.md)、[public](../cpp/public-cpp.md) 和 [protected](../cpp/protected-cpp.md)。  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)