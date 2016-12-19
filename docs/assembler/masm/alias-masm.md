---
title: "ALIAS (MASM) | Microsoft Docs"
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
  - "Alias"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALIAS directive"
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ALIAS (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**别名** 指令创建一个替代名称。功能。  这使您可以创建多个名称函数或创建允许链接器的库 \(link.exe\) 映射早期功能到新功能。  
  
## 语法  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### 参数  
 `actual-name`  
 函数或过程的实际名称。  需要尖括号。  
  
 `alias`  
 备用项或别名。  需要尖括号。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)