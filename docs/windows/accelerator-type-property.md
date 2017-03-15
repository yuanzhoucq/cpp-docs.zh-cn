---
title: "快捷键 Type 属性 | Microsoft Docs"
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
  - "Type 属性"
  - "VIRTKEY"
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 快捷键 Type 属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

快捷键的 **Type** 属性确定与快捷键 ID 关联的快捷组合键是虚拟组合键还是 ASCII\/ANSI 键值：  
  
-   如果 **Type** 属性是 **ASCII**，则 [Modifier](../windows/accelerator-modifier-property.md) 只能是 None 或 Alt，或者可以有使用 Ctrl 键的快捷键（通过在键的前面加 ^ 来指定）。  
  
-   如果 **Type** 属性是 **VIRTKEY**，则 Modifier 和 Key 值的任意组合都有效。  
  
    > [!NOTE]
    >  如果要向快捷键对应表中输入值并将此值视为 ASCII\/ANSI，只需在表中单击该项的“类型”并从下拉列表中选择“ASCII”。  然而，如果使用**“键入的下一个键”**命令（**“编辑”**菜单）指定 Key，则必须在输入 Key 代码之前将 **Type** 属性从 VIRTKEY 更改为 ASCII。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Setting Accelerator Properties](../windows/setting-accelerator-properties.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)