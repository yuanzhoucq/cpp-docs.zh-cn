---
title: 设置快捷键属性 |Microsoft Docs
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
ms.openlocfilehash: 5d47dffb782da1094c157a7bbd21c40ab6ba9fef
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606699"
---
# <a name="setting-accelerator-properties"></a>设置快捷键属性

可以设置快捷键属性[属性窗口](/visualstudio/ide/reference/properties-window)在任何时间。 此外可以使用**Accelerator**编辑器修改快捷键对应表中的快捷键属性。 使用所做更改**属性**窗口或**Accelerator**编辑器具有相同的结果： 在快捷键对应表中都即时反映编辑。

有三个属性的每个加速器[ID](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160):

- [Modifier 属性](../windows/accelerator-modifier-property.md)设置快捷键的组合键的控件。

   > [!NOTE]
   > 在中**属性**窗口中，此属性显示为三个单独的布尔属性，所有这些可独立控制： **Alt**， **Ctrl**，以及**Shift**。

- [键属性](../windows/accelerator-key-property.md)设置实际用作快捷键的键。

- [类型属性](../windows/accelerator-type-property.md)确定键被解释为虚拟 (VIRTKEY) 或 ASCII/ANSI。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[预定义快捷键](../windows/predefined-accelerator-keys.md)  
[资源编辑器](../windows/resource-editors.md)  
[快捷键编辑器](../windows/accelerator-editor.md)