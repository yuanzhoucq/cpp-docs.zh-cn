---
title: "Changing a Symbol&#39;s Numeric Value | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.changing.value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numeric values"
  - "symbols, numeric values"
  - "numeric values, changing symbols"
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Changing a Symbol&#39;s Numeric Value
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于与单个资源关联的符号，可以使用[属性窗口](../Topic/Properties%20Window.md)更改符号值。  可以使用[“资源符号”对话框](../windows/resource-symbols-dialog-box.md)更改当前未分配给资源的符号的值。  有关详细信息，请参阅[更改未分配的符号](../windows/changing-unassigned-symbols.md)。  
  
### 更改分配给单个资源或对象的符号值  
  
1.  在[资源视图](../windows/resource-view-window.md)中，选择资源。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**“属性”**窗口中，输入后跟一个等号的符号名，并在**“ID”**框中输入整数，例如：  
  
    ```  
    IDC_EDITNAME=5100  
    ```  
  
 下次保存项目时，新值会存储在符号头文件中。  只有符号名在 ID 框中保持可见；等号和值在进行验证之后不会显示。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Symbol Value Restrictions](../windows/symbol-value-restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)