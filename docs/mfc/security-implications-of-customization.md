---
title: "自定义对安全有何影响 | Microsoft Docs"
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
  - "MFC 功能包, 安全性"
  - "安全性, MFC 功能包"
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自定义对安全有何影响
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题中讨论 MFC 潜在的安全漏洞。  
  
## 潜在的安全漏洞  
 MFC 允许用户自定义应用程序的用户界面，例如，图标和按钮外观的外观。  MFC 还支持用户定义的工具，使用户执行命令 shell。  因为应用程序的自定义设置。在注册表，用户配置文件将出现安全漏洞。  访问注册表的人可以编辑那些设置和更改应用程序的外观或行为。  例如，一台计算机的管理员可以通过生成用户的应用程序模拟用户执行任何程序 \(即使从网络共享\)。  
  
## 问题解决  
 我们建议采用这三种方法中的任意一个关闭注册表中的漏洞：  
  
-   加密其中存储的数据  
  
-   存储在安全文件中的数据而不是注册表。  
  
     若要完成这些后两种方法之一，从 [CSettingsStore Class](../mfc/reference/csettingsstore-class.md) 中派生一个类并重写其方法实现加密或存储在注册表中。  
  
-   还可以禁用应用程序的自定义。  
  
## 请参阅  
 [MFC 自定义](../mfc/customization-for-mfc.md)