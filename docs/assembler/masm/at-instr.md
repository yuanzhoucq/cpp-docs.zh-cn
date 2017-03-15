---
title: "@InStr | Microsoft Docs"
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
  - "@InStr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "@InStr symbol"
ms.assetid: 980d5b9f-2b88-4306-8955-df6cd2133e68
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# @InStr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

查找 *string2* 第一次出现在 *string1 的*宏，开始在 *string1 中的* *位置* 。  如果此 *位置* 未出现，搜索以在 *string1*开头。  ; 如果未找到，则返回位置整数或 0 *string2* 。  
  
## 语法  
  
```  
  
@InStr( [[position]], string1, string2 )  
```  
  
## 请参阅  
 [Symbols Reference](../../assembler/masm/symbols-reference.md)