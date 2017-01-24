---
title: ".STACK | Microsoft Docs"
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
  - ".STACK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".STACK directive"
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .STACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当使用 [.MODEL](../../assembler/masm/dot-model.md)，定义了堆栈段 \(与段名堆栈\)。  选项 `size` 针对堆栈 \(默认值 1,024\) 指定字节数。  `.STACK` 指令自动关闭堆栈语句。  
  
## 语法  
  
```  
  
.STACK [[size]]  
```  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)