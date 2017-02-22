---
title: "对联合的不正确访问 | Microsoft Docs"
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
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 对联合的不正确访问
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.3.2.3** 使用不同类型的成员访问联合对象的成员  
  
 如果声明两个类型的联合并存储一个值，但使用其它类型访问该联合，则结果是不可靠的。  
  
 例如，声明 **float** 和 `int` 的联合。  存储一个 **float** 值，但程序稍后会将该值作为 `int` 进行访问。  在这种情况下，值取决于 **float** 值的内部存储区。  整数值是不可靠的。  
  
## 请参阅  
 [结构、联合、枚举和位域](../c-language/structures-unions-enumerations-and-bit-fields.md)