---
title: "nullptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "nullptr_cpp"
  - "nullptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nullptr 关键字 [C++]"
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nullptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 `std::nullptr_t` 类型的 null 指针常量，该类型可转换为任何原始指针类型。尽管您可以使用关键字 `nullptr` 而不包含任何标头，但如果您的代码使用类型 `std::nullptr_t`，则您必须通过包含标头 `<cstddef>` 来定义该类型。  
  
> [!NOTE]
>  用于托管代码应用程序的 C\+\+\/CLI 中也定义了 `nullptr` 关键字，并且它与 ISO 标准 C\+\+ 关键字不可互换。  如果可以使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 编译器选项（以托管代码为目标）编译代码，则在必须保证编译器使用本机 C\+\+ 解释的任何代码行中使用 `__nullptr`。  有关详细信息，请参阅 [nullptr](../windows/nullptr-cpp-component-extensions.md)。  
  
## 备注  
 请避免将 `NULL` 或零 \(`0`\) 用作 null 指针常量；`nullptr` 不仅不易被误用，并且在大多数情况下使用效果更好。例如，给定 `func(std::pair<const char *, double>)`，那么调用 `func(std::make_pair(NULL, 3.14))` 会导致编译器错误。宏 NULL 将扩展到 `0`，以便调用 `std::make_pair(0, 3.14)` 将返回 `std::pair<int, double>`，此结果不可转换为 func\(\) 的 `std::pair<const char *, double>` 参数类型。调用 `func(std::make_pair(nullptr, 3.14))` 将会成功编译，因为 `std::make_pair(nullptr, 3.14)` 返回 `std::pair<std::nullptr_t, double>`，此结果可转换为 `std::pair<const char *, double>`。  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)