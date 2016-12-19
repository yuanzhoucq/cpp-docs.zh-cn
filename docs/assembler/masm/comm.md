---
title: "COMM | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COMM"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMM directive"
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# COMM
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 `definition`指定的属性创建公共变量。  
  
## 语法  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## 备注  
 每 `definition` 具有以下形式:  
  
 \[*langtype*\[\] \[\] \[**在周围** &#124;\]\] *label***:**`type`\[\] \[**:***计数*\]  
  
 *标签* 是变量的名称。  `type` 可以是任何类型说明符 \([字节](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)，等等\) 或指定字节数的整数。  *计算* 指定数据对象数 \(一个这是默认值\)。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)