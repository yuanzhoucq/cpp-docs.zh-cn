---
title: "错误 C1113 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1113"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1113"
ms.assetid: 1c7c3ce7-2827-4822-9c63-0abc8615ea39
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 错误 C1113
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在“file”上 \#using 失败  
  
 只有 Microsoft 中间语言 \(MSIL\) 格式的文件可以传递给 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指令。  [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译器选项使您可以创建 MSIL 输出文件。  其他 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 语言也生成 MSIL 文件。