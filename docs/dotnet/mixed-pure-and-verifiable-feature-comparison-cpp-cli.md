---
title: "混合、纯 MSIL 和可验证编译模式的功能比较 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "混合程序集 [C++]"
  - "混合程序集 [C++], 与纯程序集比较"
  - "混合程序集 [C++], 与安全 MSIL 比较"
  - "纯程序集 [C++]"
  - "纯 MSIL [C++]"
  - "纯 MSIL [C++], 与混合 MSIL 和安全 MSIL 比较"
  - "纯 MSIL [C++], 与混合程序集比较"
  - "纯 MSIL [C++], 与安全 MSIL 比较"
  - "安全程序集 [C++]"
  - "安全程序集 [C++], 与混合程序集比较"
  - "安全程序集 [C++], 与纯程序集比较"
  - "可验证程序集 [C++]"
  - "可验证程序集 [C++], 与混合程序集比较"
  - "可验证程序集 [C++], 与纯程序集比较"
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 混合、纯 MSIL 和可验证编译模式的功能比较 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题比较了不同 **\/clr** 编译模式的功能。  有关详细信息，请参阅[\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 功能比较  
  
|功能|混合代码 \(\/clr\)|纯代码 \(\/clr:pure\)|安全代码 \(\/clr:safe\)|相关信息|  
|--------|--------------------|------------------------|-------------------------|----------|  
|CRT 库|支持|支持||[按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC\/ATL|支持|||[MFC 桌面应用程序](../mfc/mfc-desktop-applications.md) &#124; [Class Overview](../atl/atl-class-overview.md)|  
|非托管函数|支持|||[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)|  
|非托管数据|支持|支持||[纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|可从非托管函数中调用|支持|||[如何：迁移到 \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)|  
|支持调用非托管函数|支持|仅限于 C 样式函数|仅限于 P\/Invoke|[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|支持反射|仅限于 DLL|支持|支持|[反射](../dotnet/reflection-cpp-cli.md)|  
  
## 请参阅  
 [纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)