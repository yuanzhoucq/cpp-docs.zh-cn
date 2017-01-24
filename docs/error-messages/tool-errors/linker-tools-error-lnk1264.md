---
title: "链接器工具错误 LNK1264 | Microsoft Docs"
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
  - "LNK1264"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1264"
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1264
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已指定 \/LTCG:PGINSTRUMENT 但没有所需的代码生成；检测失败  
  
 指定了 **\/LTCG:PGINSTRUMENT**，但未找到用 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译的 .obj 文件。  检测无法发生，链接失败。  命令行上必须至少有一个用 **\/GL** 编译的 .obj 文件，这样检测才能发生。  
  
 按配置优化 \(PGO\) 仅在 64 位编译器中可用。