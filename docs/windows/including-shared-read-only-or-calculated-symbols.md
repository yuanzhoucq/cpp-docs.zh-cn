---
title: "Including Shared (Read-Only) or Calculated Symbols | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.shared.calculated"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbols, read-only"
  - "symbols, shared"
  - "symbols, calculated"
  - "read-only symbols"
  - "symbol directives"
  - "calculated symbols"
  - "shared symbols"
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Including Shared (Read-Only) or Calculated Symbols
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

开发环境首次读取由其他应用程序创建的资源文件时，会将所有包含的头文件都标记为只读。  随后，你可以使用[“资源包括”对话框](../windows/resource-includes-dialog-box.md)添加其他只读符号头文件。  
  
 可能要使用只读符号定义的原因之一是用于计划在多个项目之间共享的符号文件。  
  
 当现有资源包含的符号定义使用表达式而不是简单整数来定义符号值时，也可以使用包含的符号文件。  例如:  
  
```  
#define   IDC_CONTROL1 2100  
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```  
  
 只要满足以下条件，环境便会正确解释这些计算的符号：  
  
-   计算的符号置于只读符号文件中。  
  
-   资源文件包含已分配有这些计算的符号的资源。  
  
-   需要数值表达式。  
  
> [!NOTE]
>  如果需要字符串或数值表达式，则不会计算表达式。  
  
### 在资源文件包含共享（只读）符号  
  
1.  在[“资源视图”](../windows/resource-view-window.md)中，右键单击 .rc 文件，然后从快捷菜单中选择[“资源包括”](../windows/resource-includes-dialog-box.md)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**“只读符号指令”**框中，使用 **\#include** 编译器指令指定要在其中保留只读符号的文件。  
  
     请勿调用文件 Resource.h，因为这是通常由主符号头文件使用的文件名。  
  
    > [!NOTE]
    >  **重要事项** 在“只读符号指令”框中输入的内容会完全按照输入包含在资源文件中。  请确保输入的内容不包含任何拼写或语法错误。  
  
     使用**“只读符号指令”**框可仅包含具有符号定义的文件。  请勿包含资源定义；否则，在保存文件时会创建重复的资源定义。  
  
3.  将符号置于指定的文件中。  
  
     采用这种方式包含的文件中的符号会在每次打开资源文件时进行计算，但是在保存文件时不会在磁盘上替换它们。  
  
4.  单击“确定”。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Symbol Name Restrictions](../windows/symbol-name-restrictions.md)   
 [Symbol Value Restrictions](../windows/symbol-value-restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)