---
title: "按配置文件优化错误 PG0165 | Microsoft Docs"
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
  - "PG0165"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PG0165"
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 按配置文件优化错误 PG0165
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

正在读取“Filename.pgd”:“不支持 PGD 版本\(版本不匹配\)”。  
  
 PGD 文件特定于特定的编译器工具集。  如果正在使用的编译器与用于 *Filename*.pgd 的编译器不同，则会生成此错误。  此错误指示，此编译器工具集无法使用 *Filename*.pgd 中的数据来优化当前程序。  
  
 若要解决此问题，请使用当前的编译器工具集重新生成 *Filename*.pgd。