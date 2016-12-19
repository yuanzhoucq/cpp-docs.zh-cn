---
title: "错误 C1128 | Microsoft Docs"
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
  - "C1128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1128"
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1128
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

节数超过对象文件格式限制:请使用 \/bigobj 进行编译  
  
 .obj 文件超出了可允许的节数，COFF 对象文件格式限制。  
  
 达到这一节限制可能是因为使用了 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 和调试版本；**\/Gy** 导致函数进入自己的 COMDAT 节。  在调试版本中，每一 COMDAT 函数都有一个调试信息节。  
  
 内联函数过多时也可能导致 C1128。  
  
 若要更正此错误，请将源文件划分为多个源代码文件，在不使用 **\/Gy** 的情况下进行编译，或者使用[\/bigobj（增加 .Obj 文件中的节数）](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)进行编译。如果不使用 **\/Gy** 进行编译，则需要单独指定优化，因为 **\/O2** 和 **\/O1** 均暗指 **\/Gy**。  
  
 请尽可能不使用调试信息进行编译。  
  
 可能需要在单独的源代码文件中具有特定的模板实例，而不是让编译器发出它们。  
  
 移植代码的时候，使用 x64 编译器时 C1128 将首先出现，接下来随着 x86 编译器会出现更多。 x64将以下至少 4 个节与用 **\/Gy** 编译的或从模板或内联类进行内联的各个函数相关联：代码、pdata 和调试信息，此外可能还有 xdata。X86 没有 pdata。