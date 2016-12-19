---
title: "编译器警告（等级 1）C4041 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4041"
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制 : 正在终止浏览器输出  
  
 浏览器信息超出了编译器限制。  
  
 使用 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)（浏览器信息包含局部变量）进行编译可能导致该警告。  
  
### 使用以下可能的解决方案进行修复  
  
1.  使用 \/Fr（浏览器信息不含局部变量）进行编译。  
  
2.  禁用浏览器输出（不使用 \/FR 或 \/Fr 进行编译）。