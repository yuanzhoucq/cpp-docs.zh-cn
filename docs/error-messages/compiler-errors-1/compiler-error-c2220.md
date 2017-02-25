---
title: "编译器错误 C2220 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2220"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2220"
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C2220
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

视为错误的警告，没有生成对象文件  
  
 [\/WX](../../build/reference/compiler-option-warning-level.md) 通知编译器将所有警告视为错误。  因为发生错误，所以未生成对象或可执行文件。  
  
 此错误仅在设置**\/WX** 标志时显示 ，并且警告是在编译时出现。  若要修复此错误，必须消除项目中的每个警告。  
  
### 若要修复，请使用以下技术之一  
  
-   解决您的项目中引起警告的问题。  
  
-   在较低警告等级中编译——例如，使用 **\/W3** 而不是 **\/W4**。  
  
-   使用 [警告](../../preprocessor/warning.md) 杂注来禁用或禁止特定的警告。  
  
-   不要使用 **\/WX** 来编译。