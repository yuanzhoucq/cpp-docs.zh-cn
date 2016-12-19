---
title: "underlying_type 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "underlying_type"
  - "std.underlying_type"
  - "std::underlying_type"
  - "type_traits/std::underlying_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "underlying_type"
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# underlying_type 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成枚举类型的基础整数的类型。  
  
## 语法  
  
```  
template <class T>  
    struct underlying_type;  
```  
  
#### 参数  
 `T`  
 要修改的类型。  
  
## 备注  
 `type` 模板类的成员 typedef 名称的基础整数类型 `T`, ，当 `T` 是枚举类型，否则没有任何成员 typedef `type`。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)