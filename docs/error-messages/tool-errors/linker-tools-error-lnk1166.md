---
title: "链接器工具错误 LNK1166 | Microsoft Docs"
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
  - "LNK1166"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1166"
ms.assetid: d69548a8-0efb-44e1-90b7-b27636a4b575
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1166
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法在 offset\=offset, va\=value 处调整代码。  
  
 LINK 未能按需要填充代码。  
  
 在一些处理器上，不允许某些指令跨页边界。  LINK 尝试添加填充代码来纠正这种情况。  但用这种方法，LINK 未能解决问题。