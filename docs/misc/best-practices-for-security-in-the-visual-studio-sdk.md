---
title: "Visual Studio SDK 中安全性的最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安全性 [Visual Studio SDK]"
  - "用户帐户控制 [Visual Studio SDK]"
  - "Visual Studio SDK, 安全性"
  - "UAC（用户帐户控制）[Visual Studio SDK]"
  - "安全性最佳做法, Visual Studio SDK"
  - "Windows Vista, 用户帐户控制 [Visual Studio SDK]"
ms.assetid: 56c8a113-0c53-4969-a009-a2ab58d855c3
caps.latest.revision: 30
caps.handback.revision: 30
manager: "douge"
---
# Visual Studio SDK 中安全性的最佳做法
你需要了解 VSPackage 扩展的安全性，以便能够创建最好的产品。  
  
 安全产品有助于保护以下内容：  
  
-   客户信息的保密性、完整性和可用性。  
  
-   在系统所有者或管理员的控制下处理资源的完整性和可用性。  
  
## 安全漏洞  
 安全漏洞一直是产品存在的弱点，即使正确使用产品，也无法防止攻击者的恶意活动。 下面是一些可能的恶意活动：  
  
-   获取高于这些用户计算机上的权限。  
  
-   接管用户计算机的操作。  
  
-   危及用户计算机上的数据。  
  
> [!IMPORTANT]
>  绝不要假设将仅在特定环境中运行你的应用程序。 你的应用程序也可能用于你不希望的设置，尤其是当应用程序变得受欢迎时。 而是假设你的代码将在恶意环境中运行，并相应地设计、编写、测试你的代码。  
  
 将安全性作为一项主要功能而设计和构建的产品和系统比事后考虑到安全性而编写的那些产品和系统更可靠。 安全产品更不易受到媒体批评的影响、对用户更具吸引力，并且支持和升级的成本更低。  
  
## 危险的 API  
 如果使用不正确，对某些函数的调用可能会产生不需要的安全漏洞，而禁止使用不一定会生成安全代码。 不过，某些软件项目通过禁止难以安全使用的函数已获得了可观的益处，这是很多安全开发的实践之一。 有关详细信息，请参阅 Microsoft Press 书籍（Michael Howard 和 David LeBlanc 编著的“Writing Secure Code”）的附录 A。  
  
 大多数安全问题都是由于对信任输入未进行充分验证导致的。 请确保在数据进入代码时对其进行跟踪，并对该数据上的操作的含义持怀疑态度。 如果数据输入格式正确并且已检查可信度，则可以通过使用大多数函数编写安全代码。  
  
## 用户帐户控制 \(UAC\) 问题  
 用户帐户控制 \(UAC\) 功能存在安全隐患，你应了解这些隐患。 该功能减少了操作系统和应用程序受到恶意攻击的风险。  
  
1.  有关 [!INCLUDE[win7](../build/includes/win7_md.md)] 的 UAC 的详细信息，请参阅[什么是用户帐户控制？](http://go.microsoft.com/fwlink/?linkid=159927)。  
  
2.  有关 [!INCLUDE[win8](../build/includes/win8_md.md)] 的 UAC 的详细信息，请参阅[什么是用户帐户控制设置？](http://windows.microsoft.com/windows-8/what-are-uac-settings)。  
  
 在 UAC 出现之前，即使不需要管理员权限，开发人员通常也是在管理员权限下运行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。 你应该以普通用户身份开发和测试你的扩展，这样可以确保它不需要不必要的提升权限。  
  
 请注意，UAC 还会影响部署。 必须正确编写安装包以支持 UAC。 错误编写的包通常会导致“拒绝访问”错误，因为安装程序会尝试使用普通用户权限来执行需要提升权限的任务。  
  
## 请参阅  
 [在 Vspackage 中安全性的最佳做法](../Topic/Best%20Practices%20for%20Security%20in%20VSPackages.md)   
 [创建安全应用程序的资源](http://msdn.microsoft.com/zh-cn/0ebf5f69-76f2-498a-a2df-83cf3443e132)   
 [安全性的基础概念](../Topic/Key%20Security%20Concepts.md)