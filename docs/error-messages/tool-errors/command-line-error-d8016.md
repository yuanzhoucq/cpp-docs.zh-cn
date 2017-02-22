---
title: "命令行错误 D8016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D8016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8016"
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 命令行错误 D8016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“option1”和“option2”命令行选项不兼容  
  
 这些命令行选项不能在一起指定。  
  
 针对选项规范检查环境变量，如 CL。  
  
 **\/clr** 暗指 **\/EHa**，而且您不能使用 **\/clr** 指定任何其他 **\/EH** 编译器选项。  有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 更新 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 6.0 项目后可能会得到 D8016 错误：项目更新向导进程可能会为项目中的每个源代码文件启用 **\/RTC**，这会重写项目的 **\/RTC** 设置。若要解决这一问题，请将项目中每个源代码文件的 **\/RTC** 设置更改为默认设置，这意味着 **\/RTC**  的项目设置将对每个文件生效。  
  
 有关更改 **\/RTC** 属性设置的信息，请参见 [\/RTC（运行时错误检查）](../../build/reference/rtc-run-time-error-checks.md)。