---
title: "项目类型不可用 | Microsoft Docs"
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
  - "vs.projecttypenotavailable"
helpviewer_keywords: 
  - "“项目类型不可用”错误"
ms.assetid: a579fe75-efa2-4dd0-b5d7-ae106d3aedbd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 项目类型不可用
此对话框显示错误“由于此版本应用程序不支持项目 \<project\> 的项目类型 \<project type\>，因此无法打开该项目。”  
  
## 解决方法  
  
-   之所以会出现此对话框，是因为找不到可以打开指定文件的产品或产品版本。  尝试打开所安装的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本无法打开的项目文件时，通常会出现此错误。  例如，尝试使用 [!INCLUDE[vbprvbxprlong](../misc/includes/vbprvbxprlong_md.md)]打开 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 项目文件，就会打开此对话框。  
  
#### 解决此错误  
  
-   安装 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的正确版本。  
  
## 请参阅  
 [移植、迁移和升级 Visual Studio 项目](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md)   
 [项目属性引用](../Topic/Project%20Properties%20Reference.md)