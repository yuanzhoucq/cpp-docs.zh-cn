---
title: "使用 abort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abort 函数"
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用 abort
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

调用 [abort](../c-runtime-library/reference/abort.md) 函数会导致立即中止。  它绕过初始化的全局静态对象的一般析构过程。  它还绕过使用 `atexit` 函数指定的任何特殊处理。  
  
## 请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)