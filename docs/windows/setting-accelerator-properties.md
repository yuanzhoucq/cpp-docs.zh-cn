---
title: 设置快捷键属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5198fc1958863d3b5ad560ffeb8c5576506e9e46
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="setting-accelerator-properties"></a>设置快捷键属性
你可以在设置快捷键属性[属性窗口](/visualstudio/ide/reference/properties-window)在任何时间。 还可以使用快捷键编辑器修改快捷键对应表中的快捷键属性。 使用“属性”窗口或快捷键编辑器所做的更改具有相同结果：在快捷键对应表中都即时反映编辑情况。  
  
 有三个属性，每个快捷键[ID](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-   [Modifier 属性](../windows/accelerator-modifier-property.md)设置快捷键的键组合的控件。  
  
    > [!NOTE]
    >  在“属性”窗口中，该属性作为三个独立的 Boolean 属性出现，这三个属性均可独立控制：Alt、Ctrl 和 Shift。  
  
-   [的键属性](../windows/accelerator-key-property.md)设置实际用作快捷键的键。  
  
-   [键入属性](../windows/accelerator-type-property.md)决定是否将该键解释为虚拟的 (VIRTKEY) 还是 ASCII/ANSI。  
  

  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [预定义的快捷键](../windows/predefined-accelerator-keys.md)   
 [资源编辑器](../windows/resource-editors.md)   
 [快捷键编辑器](../windows/accelerator-editor.md)