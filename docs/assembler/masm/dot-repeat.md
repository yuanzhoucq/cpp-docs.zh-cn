---
title: ".REPEAT | Microsoft Docs"
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
  - ".REPEAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".REPEAT directive"
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .REPEAT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成重复 *语句* 块执行的代码，直到 `condition` 变为 true。  [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，变为 true，则 CX 为零时，可以通过 [.UNTIL](../../assembler/masm/dot-until.md)进行替换。  `condition` 到 **.UNTILCXZ**是可选的。  
  
## 语法  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)