---
title: "Creating New Symbols | Microsoft Docs"
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
  - "vc.editors.symbol.creating"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "New Symbol dialog box"
  - "symbols, creating"
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating New Symbols
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

开始新项目时，你可能会发现在创建将所需符号名分配给的资源之前标出这些名称会十分方便。  
  
### 使用资源符号对话框创建新符号  
  
1.  在[“资源符号”对话框](../windows/resource-symbols-dialog-box.md)中，单击**“新建”**。  
  
2.  在**“名称”**框中，输入符号名。  
  
3.  接受分配的符号值。  
  
     \- 或 \-  
  
     在**“值”**框中，输入新值。  
  
4.  单击**“确定”**以将新符号添加到符号列表。  
  
 如果输入的符号名已存在，则会出现一个消息框，表明已定义具有该名称的符号。  无法定义具有相同名称的两个或多个符号，但是可以定义具有相同数值的不同符号。  有关详细信息，请参阅[符号名限制](../windows/symbol-name-restrictions.md)和[符号值限制](../windows/symbol-value-restrictions.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Viewing Resource Symbols](../windows/viewing-resource-symbols.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)