---
title: "Blocks | Microsoft Docs"
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
  - "块"
  - "复合语句"
  - "函数定义, 代码中的块"
  - "语句, 复合"
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Blocks
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含在大括号 \(**{ }**\) 中的声明、定义和语句的序列称为“块”。在 C 中，有两种类型的块。  “复合语句”（由一个或多个语句构成的语句，请参阅[复合语句](../c-language/compound-statement-c.md)）是一种类型的块。  另一种类型的块是“函数定义”，它由一个复合语句（函数的主体）和函数的关联的“标头”（函数名称、返回类型和形参）构成。  一个块位于其他块中的情况称作“嵌套”。  
  
 请注意，当所有复合语句包含在大括号内时，并非大括号内的所有内容都构成复合语句。  例如，虽然数组、结构或枚举元素的说明可出现在大括号内，但它们不是复合语句。  
  
## 请参阅  
 [源文件和源程序](../c-language/source-files-and-source-programs.md)