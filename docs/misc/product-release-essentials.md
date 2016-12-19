---
title: "产品版本基础知识 | Microsoft Docs"
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
  - "部署, 基础知识"
  - "安装 [Visual Studio SDK], 基础知识"
ms.assetid: 28370bc8-f3a7-4c5e-9b35-8331cda14ff4
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 产品版本基础知识
关于 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成产品，一种令人愉快和倍感可靠的安装体验会给用户留下持久印象。 同样，令人不快的安装体验也会留下持久印象，因此，在安装程序开发和测试中应遵循最佳做法。  
  
## 开发 Windows Installer 安装包  
 Windows Installer 是建议安装和配置的适用于 Windows 和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成产品的服务。  
  
> [!NOTE]
>  用于安装 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成产品的 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 文档基于 Windows Installer 概念，但它不涵盖 Windows Installer 本身。 有关指向 Windows Installer 文档的相关章节的链接，请参阅下表。  
  
 在安装上下文中，*“组件”*指的是 Windows Installer 组件。 组件包含资源（如文件和注册表项），并且作为一个单元进行安装和删除。  
  
|任务|有关详细信息，请参见|  
|--------|----------------|  
|了解有关 Windows Installer 的详细信息。|[Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx)|  
|确定你的 VSPackage 的系统要求。|-   [检测系统要求](../Topic/Detecting%20System%20Requirements.md)|  
|了解如何在安装包中注册 VSPackage。|-   [VSPackage 注册](../Topic/VSPackage%20Registration.md)<br />-   [必须在安装后运行的命令](../Topic/Commands%20That%20Must%20Be%20Run%20After%20Installation.md)|  
|请参阅示例安装包。|-   IronPython 集成安装示例|  
  
## 支持并行产品  
 并行（有时缩写为*“SxS”*）指的是能够安装同一产品的多个版本，甚至能够同时运行。 关于 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成产品，它还指这一事实：[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 本身支持并行执行。  
  
|任务|有关详细信息，请参见|  
|--------|----------------|  
|了解有关在你的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成产品中支持 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的多个版本的信息。|-   [共享和版本控制的 Vspackage 之间进行选择](../Topic/Choosing%20Between%20Shared%20and%20Versioned%20VSPackages.md)<br />-   [组件管理](../Topic/Component%20Management.md)|  
|了解有关支持你的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成产品的信息。|-   [共享和版本控制的 Vspackage 之间进行选择](../Topic/Choosing%20Between%20Shared%20and%20Versioned%20VSPackages.md)<br />-   [注册由并行部署的文件扩展名](../Topic/Registering%20File%20Name%20Extensions%20for%20Side-By-Side%20Deployments.md)<br />-   [检测系统要求](../Topic/Detecting%20System%20Requirements.md)<br />-   [必须在安装后运行的命令](../Topic/Commands%20That%20Must%20Be%20Run%20After%20Installation.md)|  
  
## 测试你的 Visual Studio 集成产品  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成测试 \(VSIT\) 套件是一系列测试，用于验证 VSPackage 是否正确集成到 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中。 VSIT 不会测试 VSPackage 的功能，但有助于确保 VSPackage 不对其他 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 功能产生不利影响。 有关详细信息，请参阅 [Visual Studio 集成测试](http://msdn.microsoft.com/zh-cn/8d741735-7d93-46c2-ab93-01da7a0e016d)。