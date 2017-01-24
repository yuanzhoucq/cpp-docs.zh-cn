---
title: ".CODE | Microsoft Docs"
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
  - ".CODE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".CODE directive"
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .CODE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当使用 [.MODEL](../../assembler/masm/dot-model.md)，指示代码段的开头。  
  
## 语法  
  
```  
.CODE [[name]]  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|`name`|指定代码段的名称可选参数。  默认名称是细微，小，以简洁、稳定的 [设计](../../assembler/masm/dot-model.md)的 \_TEXT。  默认名称为其他模型中的 *modulename*\_TEXT。|  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)