---
title: "错误 C1192 | Microsoft Docs"
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
  - "c1192"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1192"
ms.assetid: 54cff717-a3eb-471d-9bd4-1c2e673dbbef
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1192
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在“file”上 \#using 失败  
  
 只有 Microsoft 中间语言 \(MSIL\) 格式的文件可以传递给 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指令。  [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译器选项使您可以创建 MSIL 输出文件。  其他 Visual Studio 语言也产生 MSIL 文件。