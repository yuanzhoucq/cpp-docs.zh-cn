---
title: "错误 C1382 | Microsoft Docs"
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
  - "C1382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1382"
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在生成“.obj”后已重新生成 PCH 文件“file”。请重新生成此对象  
  
 在使用 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) 时，编译器检测出 .pch 文件比指向它的 CIL .obj 新。  CIL .obj 文件中的信息已过期。  重新生成对象。  
  
 如果用 **\/Yc** 进行编译，但还将多个源代码文件传递给编译器，则也可能发生 C1382。若要解决此问题，请在将多个源代码文件传递给编译器时不要使用 **\/Yc**。有关详细信息，请参阅[\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md)。