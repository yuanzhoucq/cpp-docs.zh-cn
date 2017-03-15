---
title: "EXTERNDEF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXTERNDEF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXTERNDEF directive"
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EXTERNDEF
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义名为类型是 `type`*名称的* 一个或多个外部变量、标签或符号。  
  
## 语法  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## 备注  
 如果 *名称* 在模块中定义的，它将 [公共](../../assembler/masm/public-masm.md)。  如果 *名称* 在模块引用，它将 [外部](../../assembler/masm/extern-masm.md)。  如果 *名称* 引用，则将忽略此参数。  `type` 可以是 [abs](../../assembler/masm/operator-abs.md)，导入 *名称* 为常数。  通常使用包含文件。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)