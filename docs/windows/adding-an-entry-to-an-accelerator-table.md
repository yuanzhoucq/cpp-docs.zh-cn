---
title: "向快捷键对应表添加项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "添加项的快捷键表 [c + +]"
  - "“新建快捷键”命令"
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 向快捷键对应表添加项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### <a name="to-add-an-entry-to-an-accelerator-table"></a>向快捷键对应表添加项  
  
1.  通过双击中对应的图标打开快捷键对应表 [资源视图](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在快捷键对应表中右击并选择 **新的加速器** 从快捷菜单上或单击底部的表的空的行条目。  
  
3.  选择 [ID](Id%20Property.xml) 从 ID 中的下拉列表框中，或键入新 ID 采用 **ID** 框。  
  
4.  类型 [密钥](../windows/accelerator-key-property.md) 你想要使用作为加速器或右键单击，然后选择 **键入的下一步键** 从快捷菜单来设置键组合 ( **键入的下一步键** 命令也是可从 **编辑** 菜单)。  
  
5.  更改 [修饰符](../windows/accelerator-modifier-property.md) 和 [类型](../windows/accelerator-type-property.md), ，如果有必要。  
  
6.  按 **ENTER**。  
  
    > [!NOTE]
    >  确保定义的所有快捷键都是唯一的。 可以将多种组合键分配给相同 ID 而不会产生任何不良影响，例如，CTRL + P 和 F8 可以同时分配给 ID_PRINT。 但是，分配给多个 ID 的组合键会无法正常工作，例如，同时分配给 ID_SPELL_CHECK 和 ID_THESAURUS 的 CTRL + Z。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南” [](../Topic/Resources%20in%20Desktop%20Apps.md) 中的 *应用程序中的资源* 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [Walkthrough: Using Resources for Localization with ASP。NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **惠?**  
  
 Win32  
  
## <a name="see-also"></a>另请参阅  
 [编辑快捷键对应表](../windows/editing-accelerator-tables.md)   
 [快捷键编辑器](../mfc/accelerator-editor.md)