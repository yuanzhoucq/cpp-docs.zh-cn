---
title: "The dependency &#39;file&#39; cannot be found | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.supdepnotfound"
ms.assetid: a0e6e658-c723-40da-8275-fa212165bd7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The dependency &#39;file&#39; cannot be found
项目引用之一本身包含未能找到的引用（依赖项）。  
  
 当您在源代码管理下登记项目时，可能发现您的计算机上无法解析某些依赖项。  这是因为引用路径属性是一个计算机特定的属性，因此并不在源代码管理之下。  
  
### 更正此错误  
  
1.  在磁盘上找到指示的程序集引用并修改“引用路径”属性。  
  
2.  如果无法在磁盘上找到程序集文件，则可能必须重新安装 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，或者，如果无法在磁盘上找到该程序集的依赖项，则可能必须重新安装任何第三方的自定义控件。  而且，如果正在登记源代码管理的项目，则可能不得不安装该项目所需的任何第三方控件。  
  
 这种情况将不会妨碍生成项目。  但是，在运行此应用程序时可能会有一个 TypeLoadException。  同时，不会将受到影响的依赖项报告给“部署”进程。  
  
 可以在解决方案资源管理器中的**“引用”**节点中查看项目的引用。  
  
## 请参阅  
 [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/zh-cn/8e549b39-7256-456a-8fd7-089b23facf9c)