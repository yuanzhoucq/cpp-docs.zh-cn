---
title: "编译器错误 C2827 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2827"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2827"
ms.assetid: cb3e5814-0c92-40e4-b620-98578ae3003a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2827
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator operator”不能由一元格式全局重写  
  
 该运算符在对象外不能具有一元格式。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  使重载运算符成为对象的本地运算符。  
  
2.  选择要重载的适当一元运算符。