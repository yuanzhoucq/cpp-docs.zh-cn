---
title: "链接器工具错误 LNK2026 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2026"
ms.assetid: 9955bf7c-59b5-4fa1-8481-147db0d7df45
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK2026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

模块对于 SAFESEH 映像是不安全的  
  
 [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md) 已指定，但某一模块与安全异常处理功能不兼容。  如果要将此模块用于 **\/SAFESEH**，则需要使用 Visual C\+\+ .NET 2003（或更高版本）编译器重新编译该模块。