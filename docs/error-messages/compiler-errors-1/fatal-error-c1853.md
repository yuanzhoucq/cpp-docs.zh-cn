---
title: "错误 C1853 | Microsoft Docs"
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
  - "C1853"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1853"
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1853
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“filename”预编译头文件来自编译器的早期版本，或者预编译头为 C\+\+ 而在 C 中使用它\(或相反\)  
  
 可能的原因：  
  
-   预编译头文件是用前一编译器版本编译的。  尝试用当前的编译器重新编译头文件。  
  
-   预编译头为 C\+\+，而您在 C 中使用它。  通过指定 [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 编译器选项之一，或将源文件的后缀更改为“c”，尝试重新编译头文件以与 C 一起使用。  有关详细信息，请参阅[预编译代码的两种方法](../../build/reference/two-choices-for-precompiling-code.md)。