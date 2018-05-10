---
title: 向快捷键对应表中添加一个条目 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22f3e00c8ba6523f6cc615e4a766ad9206560b5e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="adding-an-entry-to-an-accelerator-table"></a>向快捷键对应表添加项
### <a name="to-add-an-entry-to-an-accelerator-table"></a>向快捷键对应表添加项  
  
1.  通过双击图标中的将其打开的快捷键对应表[资源视图](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在快捷键对应表中右击并选择**新快捷键**从快捷菜单上或在表的底部的空行条目上单击。  
  
3.  选择[ID](id-property.md)从 ID 中的下拉列表框中，或键入新 ID 采用**ID**框。  
  
4.  类型[密钥](../windows/accelerator-key-property.md)你想要用作快捷键或右键单击并选择**键入的下一个密钥**从快捷菜单来设置组合键 (**键入的下一个密钥**命令是也可从此**编辑**菜单)。  
  
5.  更改[修饰符](../windows/accelerator-modifier-property.md)和[类型](../windows/accelerator-type-property.md)，如果有必要。  
  
6.  按 Enter。  
  
    > [!NOTE]
    >  确保定义的所有快捷键都是唯一的。 可以将多种组合键分配给相同 ID 而不会产生任何不良影响，例如，CTRL + P 和 F8 可以同时分配给 ID_PRINT。 但是，分配给多个 ID 的组合键会无法正常工作，例如，同时分配给 ID_SPELL_CHECK 和 ID_THESAURUS 的 CTRL + Z。  
  

  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [编辑快捷键对应表](../windows/editing-accelerator-tables.md)   
 [快捷键编辑器](../windows/accelerator-editor.md)