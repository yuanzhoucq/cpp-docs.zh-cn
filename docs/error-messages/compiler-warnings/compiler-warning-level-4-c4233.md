---
title: "编译器警告（等级 4）C4233 | Microsoft Docs"
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
  - "C4233"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4233"
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4233
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 : 仅在 C\+\+ 中支持“keyword”关键字，C 中不支持  
  
 编译器将您的源代码编译成了 C 而不是 C\+\+，而您使用的关键字只在 C\+\+ 中有效。  如果源文件的扩展名是 .c 或者使用 [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)，则编译器将源文件编译成 C。  
  
 此警告自动升级为错误。  如果希望修改此行为，请使用 [\#pragma warning](../../preprocessor/warning.md)。  例如，若要使 C4233 成为警告等级 4 问题，  
  
```  
#pragma warning(2:4233)  
```  
  
 请在源代码文件中使用。