---
title: "可再发行组件 | Microsoft Docs"
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
  - "可再发行组件"
  - "安装 [Visual Studio SDK], 可再发行组件"
ms.assetid: 5072281f-3cb3-4985-bd93-c7981233bf92
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# 可再发行组件
[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 包括您可以将其分发给用户根据 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] SDK 许可协议的文章的代码。  这样可再发行组件包括 Windows Installer 包，而变为的一部分产品设置的合并模块过程以及您生成到您的 Vspackage 的源代码。  
  
 下表介绍 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] SDK 中包含的可再发行组件。  元素可以在 *Visual Studio SDK 安装路径*\\ VisualStudioIntegration \\ 发行找到 \\。  
  
|文件名|说明|  
|---------|--------|  
|VSSDKTestHost.exe|您可以安装此可执行文件作为安装的一部分。|  
  
## 安装可再发行组件包  
 安装可执行代码的可再发行组件提供。 Windows Installer 包 \(.msi 文件\)，以便 Microsoft 可以提供更新，如果要求他们修复安全漏洞或其他重要 bug。  
  
 由于 Windows Installer 包只允许一次安装，安装一个可再发行组件包需要使用按顺序安装多个包的单独的可执行程序。  此类程序通常称为 *链接器* 或引导程序。  
  
> [!IMPORTANT]
>  *嵌套的安装* \(也称为 *并发安装*\) 在 Windows Installer 中不鼓励，因为 “嵌套”产品无法单独进行修补。  只能由其安装的产品才修补。  由于 [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] 可再发行组件包安装文件对共享目录，并且必须支持独立修补，无法安装使用嵌套的安装，它们。  
  
## 请参阅  
 [发布产品](../misc/releasing-a-visual-studio-integration-product.md)