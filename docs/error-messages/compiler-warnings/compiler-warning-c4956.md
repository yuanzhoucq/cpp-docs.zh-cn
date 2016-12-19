---
title: "编译器警告 C4956 | Microsoft Docs"
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
  - "C4956"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4956"
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4956
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：此类型不可验证  
  
 当指定了 [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 而你的代码包含不可验证的类型时，将生成此警告。  
  
 有关更多信息，请参见[纯代码和可验证代码](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [\/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。  
  
 下面的示例生成 C4956：  
  
```  
// C4956.cpp // compile with: /clr:safe int* p;   // C4956  
```