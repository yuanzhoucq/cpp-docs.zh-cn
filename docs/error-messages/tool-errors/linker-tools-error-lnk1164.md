---
title: "链接器工具错误 LNK1164 | Microsoft Docs"
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
  - "LNK1164"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1164"
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1164
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

section 节对齐值\(number\)大于 \/ALIGN 值  
  
 对象文件中给定节的对齐大小超过用 [\/ALIGN](../../build/reference/align-section-alignment.md) 选项指定的值。  **\/ALIGN** 值必须是 2 的幂，并且必须等于或大于对象文件中给定的节对齐大小。  
  
 用较小的节对齐大小重新编译，或者增大 **\/ALIGN** 值。