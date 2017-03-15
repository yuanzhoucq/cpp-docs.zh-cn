---
title: "编译器警告（等级 4）C4057 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4057"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4057"
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 4）C4057
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: “identifier1”与“identifier2”在稍微不同的基类型间接寻址上不同  
  
 两个指针表达式引用不同的基类型。 使用表达式时无需转换。  
  
### 通过检查以下可能的原因进行修复  
  
1.  混合签名和未签名的类型。  
  
2.  混合 **short** 和 **long** 类型。