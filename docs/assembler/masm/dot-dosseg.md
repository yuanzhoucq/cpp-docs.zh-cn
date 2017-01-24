---
title: ".DOSSEG | Microsoft Docs"
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
  - ".DOSSEG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".DOSSEG directive"
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .DOSSEG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

根据 MS\-DOS 段约定对段:首先，然后代码在 DGROUP 的段不在 DGROUP，然后段。  
  
## 语法  
  
```  
  
.DOSSEG  
  
```  
  
## 备注  
 在 DGROUP 的段按照以下顺序:段不在 BSS 或堆栈，然后 BSS 段和最后堆栈段。  主要用于确保 CodeView 支持在 MASM 独立计画。  和 [DOSSEG](../../assembler/masm/dosseg.md)相同。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)