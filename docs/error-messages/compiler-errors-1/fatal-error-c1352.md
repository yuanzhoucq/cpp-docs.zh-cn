---
title: "错误 C1352 | Microsoft Docs"
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
  - "C1352"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1352"
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1352
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函数“function”\(模块“file”中\)的 MSIL 无效或已损坏  
  
 向编译器传递了一个 .netmodule 文件，但编译器检测出该文件已损坏。  向生成该 .netmodule 文件的人员询问有关情况。  
  
 编译器并不检查 .netmodule 文件中所有类型的损坏。  但它检查函数中的所有控制路径是否包含返回语句。  
  
 有关详细信息，请参阅[用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。