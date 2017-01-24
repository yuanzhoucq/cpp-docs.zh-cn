---
title: "预编译代码的两种方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 文件"
  - ".pch 文件, 预编译选项"
  - "自动预编译"
  - "代码, 预编译"
  - "编译源代码, 预编译"
  - "PCH 文件"
  - "PCH 文件, 预编译选项"
  - "预编译的头文件"
  - "预编译的头文件, 预编译选项"
  - "预编译代码"
ms.assetid: f50ac76f-e2a2-462d-bda5-0e2ab7cccdeb
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 预编译代码的两种方法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 Visual C\+\+ 可以预编译任何 C 或 C\+\+ 代码；并不仅限于预编译头文件。  
  
 预编译要求先进行规划，但如果预编译的是除简单的头文件之外的源代码，则将大幅度提高编译速度。  
  
 如果知道源文件使用一组通用的头文件但包含顺序不同，或者希望将源代码包含在预编译中，则需预编译代码。  
  
 预编译头选项为 [\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md) 和 [\/Yu（使用预编译的头文件）](../../build/reference/yu-use-precompiled-header-file.md)。  使用 **\/Yc** 创建预编译头。  与可选的 `hdrstop` 杂注一起使用时，**\/Yc** 允许对头文件和源代码都进行预编译。  选择 **\/Yu** 在现有编译中使用现有预编译头。  还可以将 **\/Fp** 与 **\/Yc** 和 **\/Yu** 选项结合使用，为预编译头提供其他名称。  
  
 **\/Yu** 和 **\/Yc** 的编译器选项参考主题讨论如何在开发环境中访问此功能。  
  
## 更多信息  
  
-   [何时需要预编译源代码](../../build/reference/when-to-precompile-source-code.md)  
  
-   [预编译头一致性规则](../../build/reference/precompiled-header-consistency-rules.md)  
  
-   [在项目中使用预编译头](../../build/reference/using-precompiled-headers-in-a-project.md)  
  
 有关使用预编译头的其他示例，请参见用于生成 Microsoft 基础类库随附的示例程序的生成文件。  
  
## 请参阅  
 [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)