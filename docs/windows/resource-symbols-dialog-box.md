---
title: "“资源符号”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.resourcesymbols"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“新建符号”对话框"
  - "“资源符号”对话框"
  - "“更改符号”对话框"
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# “资源符号”对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

借助**“资源符号”**对话框，你可以添加新的资源符号、更改显示的符号或跳到源代码中正在使用符号的位置。  
  
 **名称**  
 显示符号的名称。  有关详细信息，请参阅[符号名限制](../windows/symbol-name-restrictions.md)。  
  
 **值**  
 显示符号的数值。  有关详细信息，请参阅[符号值限制](../windows/symbol-value-restrictions.md)。  
  
 **正在使用**  
 选中后，指定符号正由一个或多个资源使用。  “使用者”框中列出一个或多个资源。  
  
 **显示只读符号**  
 选定后，显示只读资源。  默认情况下，“资源符号”对话框中仅显示资源脚本文件中可修改的资源，但通过选中此选项，可修改的资源将显示为加粗文本，而只读资源以纯文本形式显示。  
  
 **使用者**  
 显示使用符号列表中所选符号的一个或多个资源。  若要移动到给定资源的编辑器，请选择**“使用者”**框中的资源，然后单击**“查看使用”**。  有关详细信息，请参阅[打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。  
  
 **新建**  
 打开“新建符号”对话框，它可用于为新的符号资源标识符定义名称和值（若有必要）。  有关详细信息，请参阅[创建新符号](../windows/creating-new-symbols.md)。  
  
 **更改**  
 打开“更改符号”对话框，它可用于更改符号的名称或值。  如果符号针对的是使用中的控件或资源，则仅可从相应的资源编辑器更改此符号。  有关详细信息，请参阅[更改未分配的符号](../windows/changing-unassigned-symbols.md)。  
  
 **查看使用**  
 打开包含相应资源编辑器中的符号的资源。  有关详细信息，请参阅[打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Viewing Resource Symbols](../windows/viewing-resource-symbols.md)