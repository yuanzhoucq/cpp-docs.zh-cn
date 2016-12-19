---
title: "Visual Studio SDK 和托管代码 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIP，有关托管代码"
ms.assetid: 16b3d88e-b5d8-49a5-a5d7-07cbb0b7e4fc
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Visual Studio SDK 和托管代码
*托管代码* 在任何语言面向公共语言运行 \(CLR\)时 \(clr\)，例如 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]， [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]，或者 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]编写的代码。  无论该语言编写的，所有托管代码编译为 Microsoft 中间语言 \(msil\) 而不是本机代码。  
  
## 环境进行管理的 Vspackage 支持  
 若要支持创建 VSPackage 或项目中包含一个托管语言 \(如 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]， [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 提供以下内容:  
  
-   [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集，这将使托管代码编写的 Vspackage 与非托管 COM \(\) [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成开发环境 \(ide\) 兼容 \(IDE\)。  有关更多信息，请参见 [使用 Visual Studio 互操作程序集](../Topic/Using%20Visual%20Studio%20Interop%20Assemblies.md)。  
  
-   提供使用较高级别的抽象 \(MPF\)。 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 中设置托管包 framework 类。  这些类封装某些使用更频繁的接口并输入 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集。  它们大大减少必须完成 VSPackage 或项目的基本功能的工作量。  有关更多信息，请参见 [托管包框架类](../misc/managed-package-framework-classes.md)。  
  
-   在托管代码中的设置基本的一些示例。  在简单，完整功能 VSPackage 示例的管理的示例生成演示一个基本编辑、工具窗口、扩展程序对象和其他元素。  有关更多信息，请参见 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
## 请参阅  
 [托管的 VSPackage](../misc/managed-vspackages.md)   
 [使用 Visual Studio 互操作程序集](../Topic/Using%20Visual%20Studio%20Interop%20Assemblies.md)   
 [托管包框架类](../misc/managed-package-framework-classes.md)