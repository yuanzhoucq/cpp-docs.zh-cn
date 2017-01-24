---
title: "编译器警告（等级 1）C4470 | Microsoft Docs"
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
  - "C4470"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4470"
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4470
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 \/clr 下忽略了浮点控制 pragma  
  
 浮点控制 pragma：  
  
-   [fenv\_access](../../preprocessor/fenv-access.md)  
  
-   [float\_control](../../preprocessor/float-control.md)  
  
-   [fp\_contract](../../preprocessor/fp-contract.md)  
  
 在 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 下无效。  
  
 下面的示例生成 C4470：  
  
```  
// C4470.cpp  
// compile with: /clr /W1 /LD  
#pragma float_control(except, on)   // C4470  
```