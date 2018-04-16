---
title: "快捷键 Type 属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 214d8ca9c45a3657215833764268794b152bd337
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-type-property"></a>快捷键 Type 属性
快捷键**类型**属性确定是否与快捷键 ID 关联的快捷键组合为虚拟键组合或 ASCII/ANSI 密钥值：  
  
-   如果**类型**属性是**ASCII**、[修饰符](../windows/accelerator-modifier-property.md)可能仅为 None 或 Alt，也可以使用 CTRL 键的加速器 (通过在前面的密钥指定 ^)。  
  
-   如果**类型**属性是**VIRTKEY**，修饰符和密钥值的任意组合无效。  
  
    > [!NOTE]
    >  如果你想要的快捷键对应表中输入一个值，并具有值被视为 ASCII/ANSI，只需单击表中的条目的类型，从下拉列表中选择 ASCII。 但是，如果你使用**键入的下一个密钥**命令 (**编辑**菜单) 若要指定的密钥，则必须更改**类型**属性从 VIRTKEY 为 ASCII *之前*中输入密钥的代码。  
  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [设置快捷键属性](../windows/setting-accelerator-properties.md)   
 [快捷键编辑器](../windows/accelerator-editor.md)