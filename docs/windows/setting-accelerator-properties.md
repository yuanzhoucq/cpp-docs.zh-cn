---
title: "设置快捷键属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "快捷键属性"
  - "快捷键属性的属性 [c + +]"
  - "Type 属性"
  - "Key 属性"
  - "Modifier 属性"
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 设置快捷键属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual c + +.NET 中，可以设置快捷键属性 [属性窗口](../Topic/Properties%20Window.md) 在任何时间。 还可以使用快捷键编辑器修改快捷键对应表中的快捷键属性。 使用“属性”窗口或快捷键编辑器所做的更改具有相同结果：在快捷键对应表中都即时反映编辑情况。  
  
 有三个属性为每个加速器 [ID](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-    [Modifier 属性](../windows/accelerator-modifier-property.md) 设置快捷键的键组合的控件。  
  
    > [!NOTE]
    >  在“属性”窗口中，该属性作为三个独立的 Boolean 属性出现，这三个属性均可独立控制：Alt、Ctrl 和 Shift。  
  
-    [键属性](../windows/accelerator-key-property.md) 设置实际用作快捷键的键。  
  
-    [类型属性](../windows/accelerator-type-property.md) 决定是否将该键解释为虚拟键 (VIRTKEY) 还是 ASCII/ANSI。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南” [](../Topic/Resources%20in%20Desktop%20Apps.md) 中的 *应用程序中的资源* 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [Walkthrough: Using Resources for Localization with ASP。NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>另请参阅  
 [预定义的快捷键](../windows/predefined-accelerator-keys.md)   
 [资源编辑器](../mfc/resource-editors.md)   
 [快捷键编辑器](../mfc/accelerator-editor.md)