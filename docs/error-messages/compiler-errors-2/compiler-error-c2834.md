---
title: "编译器错误 C2834 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2834"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2834"
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2834
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator operator”必须被全局限定  
  
 `new` 和 `delete` 运算符被绑定到它们所驻留的类。  范围解析无法用于从不同的类选择 `new` 或 `delete` 的版本。  若要实现多种形式的 `new` 或 `delete` 运算符，请创建带有额外形参的运算符版本。