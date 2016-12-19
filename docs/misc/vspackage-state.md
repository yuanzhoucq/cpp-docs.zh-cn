---
title: "VSPackage 状态 | Microsoft Docs"
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
  - "状态, Vspackage"
  - "VSPackage, 管理应用程序状态"
  - "状态持久性"
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
caps.handback.revision: 25
manager: "douge"
---
# VSPackage 状态
许多因素确定设置保留的值或状态， [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 应用程序。  
  
-   项目具有项和配置属性。  
  
-   解决方案具有特性。  
  
-   用户设置确定大小，并且位置文档窗口，工具窗口，停靠状态和键盘快捷键。  
  
-   应用程序可能具有用户设置的选项。  
  
-   应用程序创建的对象可以有自己的特性。  
  
 这是 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 应用程序状态可管理的某些方法:  
  
-   将项目和解决方案属性页。  
  
-   通过 **导入和导出设置 " 向导**，允许用户从一台计算机将设置为另一个。  
  
-   通过 **选项** 对话框，包括选项与应用程序相关。  
  
-   通过 **属性** 窗口，其中显示对象的属性。  
  
-   通过自动化。  应用程序可以显示了自动化的访问 VSPackage 和对象属性。  
  
 基础应用程序状态是可使应用程序状态中保存和还原各种保持机制。  
  
## 本节内容  
 [状态持久性支持](../misc/support-for-state-persistence.md)  
 列表，保存和还原重置的 VSPackage 的状态常用方法。  
  
 [选项和选项页](../Topic/Options%20and%20Options%20Pages.md)  
 表示泛型和自定义选项卡页并解释如何实现它们。  
  
 [创建选项页](../Topic/Creating%20an%20Options%20Page.md)  
 解释如何创建两个选项卡页、简单的页和自定义页。  
  
 [支持设置类别](../misc/support-for-settings-categories.md)  
 讨论用户设置，以及如何创建和保存。  
  
 [创建设置类别](../Topic/Creating%20a%20Settings%20Category.md)  
 解释如何创建 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 设置类别并使用它来保存值以及从设置文件还原值。  
  
 [扩展属性和属性窗口](../Topic/Extending%20Properties%20and%20the%20Property%20Window.md)  
 解释如何显示和更改对象的值在 **属性** 窗口中。  
  
 [公开属性设置为属性窗口](../Topic/Exposing%20Properties%20to%20the%20Properties%20Window.md)  
 说明如何显示对象的公共属性。 **属性** 窗口。  
  
 [对项目和配置属性的支持](../Topic/Support%20for%20Project%20and%20Configuration%20Properties.md)  
 解释如何显示和更改项和配置属性。  
  
 [获取项目属性](../Topic/Getting%20Project%20Properties.md)  
 指导您通过一系列步骤创建显示在工具窗口的项目属性的托管 VSPackage。  
  
 [使用设置存储](../Topic/Using%20the%20Settings%20Store.md)  
 解释设置存储在持久性 framework 及使用方法。  
  
## 相关章节  
 [Vspackage](../Topic/VSPackages.md)  
 提供常规方向指向解释如何创建和使用 Vspackage 的主题。