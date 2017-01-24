---
title: "错误 C1305 | Microsoft Docs"
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
  - "C1305"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1305"
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1305
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

配置文件数据库“pgd\_file”用于不同的结构  
  
 从另一平台的 \/LTCG:PGINSTRUMENT 操作生成的 .pgd 文件传递给了 [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)。  [配置文件导引优化](../../build/reference/profile-guided-optimizations.md)可用于x86和[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]平台。  但是，使用一个平台的 \/LTCG:PGINSTRUMENT 操作生成的 .pgd 文件作为不同平台的 \/LTCG:PGOPTIMIZE 输入是无效的。  
  
 要解决此错误，只需将使用 \/LTCG:PGINSTRUMENT 创建的 .pgd 文件传递给同一平台上的 \/LTCG:PGOPTIMIZE。