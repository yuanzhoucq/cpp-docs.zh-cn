---
title: "链接器工具错误 LNK2008 | Microsoft Docs"
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
  - "LNK2008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2008"
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK2008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

链接地址信息目标不是对齐的“symbol\_name”  
  
 LINK 在对象文件中找到了未正确对齐的链接地址信息目标。  
  
 此错误可能是由于自定义的节对齐（例如 \#pragma [pack](../../preprocessor/pack.md)）、[align](../../cpp/align-cpp.md) 修饰符或使用修改节对齐的程序集语言代码引起的。  
  
 如果您的代码未使用上述任何内容，则可能是由编译器引起的。